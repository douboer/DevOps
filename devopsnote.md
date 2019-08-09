
## devops笔记

#### LB & HA & 容灾
hard LB A10，F5，据说A10的财务状况并不好啊，可见以后是SLB天下了
SLB DNS、NGX、LVS、HAproxy结合keepalived搭建
NGX利用反向代理upstream来实现负载均衡
据说Tengine在NGX基础进行了改进，但用户接受度并不高，不利于产品良性迭代，HA更重要
keepalived给HA提供保证，基于我们熟悉的VRRP协议，做容灾是很好的

四层负载均衡有LVS，七层负载均衡有Haproxy、Nginx，目前用的最多的就是这三种了

阿里云用LVS+Tengine SLB，ECS直接挂LVS，四层监听的流量直接由LVS转发到ECS，7层监听的流量会经过LVS到Tenigine再到用户ECS


问题
 - DNS不足？
 - upstream 反向代理关系？
 - LVS是什么，怎么实现？
 - 天翼云没有A10？LB怎么做
 - 跨域机房双活怎么做？
 - 性能问题？ QPS
 - docker化下与虚拟机下LB思路不同？

---
阿里服务
```
                   redis/oss/
                   monitor/log        dataV
                 |                 |
APP - CDN - WAF -|- SLB - ECS集群 -|- RDS集群
                 |                 |
```

SLB
```
+---------------------------------------------------------------+
|                      +--------------+                         |
|            ----------|   CLOUD      |----------               |
|            |         +--------------+         |               |
|  +---------+---------+             +--------------------+     |
|  |         |         |             |lvs cluster         |     |
|  | LVS cluster       |             |          |         |     |
|  |         |tengine cluster        |          tengine cluster |
|  +---------+---------+             +----------+---------+     |
|                                                               |
|                          SLB cluster                          |
+---------------------------------------------------------------+
```

CDN
<li>内容分发、复制、cache
<li>智能DNS，优化到达缓存/复制点
<li>缺点：能容可能不同步，可闲时同步

WAF价格高出SLB好多

---
#### 容器云LB技术

几个基本概念：
1. RSS/RPS/RFS/XPS的基本认识
- 对NIC出入数据的优化
- RSS(receive side scaling)，数据队列均衡到不同核，硬件实现
- RPS(Receive Packet Steering)，数据队列均衡到不同核，软件实现
  RSS和RPS都是网卡为了在接受数据包的时候使用多核架构而进行的性能增强，RSS是在硬件层面而RPS在软件层面
- RFS(Receive Flow Steering) 保证接受中断CPU内核正好是用户处理的CPU，避免转换开销
  XPS(Transmit Packet Steering) 保证发送软中断CPU内核正好是用户处理的CPU，避免转换开销

一句话，这4个东西：
  - 保证入出数据在不同核之间的均衡，
  - 保证入出数据中断和处理在同一个核心上

2. PREROUTING/POSTROUTING/SNAT/DNAT
  - 源地址发送数据--> {PREROUTING-->路由规则--> POSTROUTING}-->目的地址接收到数据
    PREROUTING是“路由规则”之前的动作，POSTROUTING是“路由规则”之后的动作
  - DNAT在PREROUTING，SNAT在POSTROUTING
  - SNAT,数据包从网卡发送出去的时候，把数据包中的源地址替换，这样，接收方认为来源被替换IP
    DNAT,数据包从网卡发送出去的时候，修改目的IP，你想访问A，DNAT后把访问A的数据包修改为访问B

3. LVS模式
  - DR
    改写目的MAC为RS MAC，LVS对用户透明，不该IP，返回直接访问CLient
    LVS&RS需在同一个二层
  - NAT
    来回都走LVS，LVS是瓶颈
    LVS&RS需在同一个二层
  - TUNNEL
    只能Linux内核支持
  - Full-NAT
    Packet IN    dest ip:LVS VIP->RS ip，src ip:CLent IP->LVS内网IP
    Packet OUT   dest ip:LVS内网IP->Clent IP, src ip: RS IP->LVS VIP

```
                             FULLNAT MODE
         +----------------  --+ PC/CLENT+-   ---------------------+
     REQUST                 |            |                        |
         |                  +------------+                        |
 SRCIP:CLIENTIP                                                 RESPONSE
 DESTIP:L^S VIP                                                   |
         |                                                    SRC:LVS VIP
         |                                                    DEST:CLIENT IP
         |                                                        |
+--------v------+             +--------------+             +------v--------+
| DNAT+SNAT     |             |   LVS        |            ++               |
|               +-------------+              +-------------+SNAT+DNAT      |
+-------+-------+             +--------------+             +------+--------+
        |                                                         |
SRC:LVS INTERNAL IP                                          SRC:RS IP
DEST:RS IP                   +---------------+               DEST: LVS INTERNAL IP
        |                    |               |                    |
        +------------------->+     RS        +<-------------------+
                             +---------------+
```


---
#### Nginx vs. LVS vs. haproxy vs. DNS
   Ngx做LB？优缺点？
   LVS 模式？优缺点？
   haproxy怎么做？优缺点
   DNS作为LVS一种模式

NGX
  七层
  正则
  配置
  日志
  做webserver
  做反向加速缓存
  http/https/mail
  社区

  ? session保持
  ? 健康检查？url检测

LVS
  四层
  流量类型支持度
  配置性
  只发请求
  :x:正则

haproxy
  session保持
  
  处理效率
  并发

  haproxy策略
    :1: roundrobin
    :2: static-rr 权重 :star:
    :3: leastconn 最少连接者先处理 :star:
    :4: source 表示根据请求源IP，这个跟Nginx的IP_hash机制类似，我们用其作为解决session问题的一种方法 :star:
    :5: ri 表示根据请求的URI
    :6: rl_param 表示根据请求的URl参数'balance url_param' requires an URL parameter name
    :7: hdr(name) 表示根据HTTP请求头来锁定每一次HTTP请求
    :8: rdp-cookie(name) 表示根据据cookie(name)来锁定并哈希每一次TCP请求


参考
1. [高性能负载均衡设计与实现](https://zhuanlan.zhihu.com/p/29949340)
2. [容器云负载均衡之三：RSS、RPS、RFS和XPS调整](https://blog.csdn.net/cloudvtech/article/details/80182074)
2. [从一个开发的角度看负载均衡和LVS](https://blog.csdn.net/daiyudong2020/article/details/51611118)
2. []()
2. []()
2. []()
