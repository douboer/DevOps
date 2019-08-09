mermaid: true

## devops笔记

#### LB & HA
hard LB A10，F5，据说A10的财务状况并不好啊，可见以后是SLB天下了
SLB DNS、NGX、LVS、HAproxy结合keepalived搭建
NGX利用反向代理upstream来实现负载均衡
据说Tengine在NGX基础进行了改进，但用户接受度并不高，不利于产品良性迭代，HA更重要
keepalived给HA提供保证，基于我们熟悉的VRRP协议

阿里云用LVS+Tengine SLB，ECS直接挂LVS，四层监听的流量直接由LVS转发到ECS，7层监听的流量会经过LVS到Tenigine再到用户ECS

问题
 - DNS不足？
 - upstream 反向代理关系？
 - LVS是什么，怎么怎么实现？
 - 天翼云没有A10？LB怎么做
 - 跨域机房双活怎么做？

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
|                      |   CLOUD      |                         |
|            ----------|              |----------               |
|            |         +--------------+         |               |
|  +---------+---------+             +--------------------+     |
|  |         |         |             |lvs cluster         |     |
|  | LVS cluster       |             |          |         |     |
|  |         |         |             |          |         |     |
|  |         |tengine cluster        |          tengine cluster |
|  |         |         |             |          |         |     |
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
Nginx vs. LVS vs. haproxy vs. DNS
9A)
