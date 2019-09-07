
## 淘宝架构演进笔记

```
 - 消除单点
 - 水平扩展
 - 跨机房多活
 - 缓存

 跨域多活数据同步问题，DRC？
```

![img](imgs/t1.jpg)

![img](imgs/t2.jpg)

#### :green_heart: 缓存
![img](imgs/t3.jpg)

#### :green_heart: LB -> NGX 7层LB， 
![img](imgs/t4.jpg)

#### :green_heart: 数据库 加入myCAT做DB读写分离
![img](imgs/t5.jpg)

#### :green_heart: Redis做缓存
![img](imgs/t6.jpg)

#### :green_heart: 数据库 业务拆分
![img](imgs/t7.jpg)

#### :green_heart: LVS+F5 做4层LB，myCAT表拆分
![img](imgs/t8.jpg)

#### :green_heart: LB DNS RR轮询 跨机房负载均衡 机房级别水平扩展
![img](imgs/t9.jpg)

#### :green_heart: 海量数据 noSQL，hBase
![img](imgs/t10.jpg)

#### :green_heart: 应用规划、拆分
![img](imgs/t11.jpg)

#### :green_heart: 微服务，公共服务提炼，dubbo，springcloud =》 治理、限流、熔断、降级
![img](imgs/t12.jpg)

#### :green_heart: 加入服务总线
![img](imgs/t13.jpg)

#### :green_heart: docker管理，屏蔽环境差异，加速部署，提升运维效率，k8s
![img](imgs/t14.jpg)

#### :green_heart: 云部署，CDN+SLB+WAF可以由云服务提供，也可以自己搭建，docker+k8s
![img](imgs/t15.jpg)



[-](https://zhuanlan.zhihu.com/p/69421196)
