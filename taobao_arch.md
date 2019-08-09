
## 淘宝从几百到千万级并发的十四次架构演进之路

![img](imgs/t1.jpg)

#### 缓存
![img](imgs/t2.jpg)

#### LB -> NGX 7层LB， 
![img](imgs/t3.jpg)

#### 数据库 加入myCAT做DB读写分离
![img](imgs/t4.jpg)

#### 数据库 业务拆分
![img](imgs/t5.jpg)

![img](imgs/t6.jpg)

#### LVS+F5 做4层LB，myCAT表拆分
![img](imgs/t7.jpg)

#### LB DNS RR轮训 跨机房负载均衡 机房级别水平扩展
![img](imgs/t8.jpg)

#### 海量数据 noSQL，hBase，Redis做缓存
![img](imgs/t9.jpg)

#### 应用规划、拆分
![img](imgs/t10.jpg)

#### 微服务，公共服务提炼，dubbo，springcloud =》 治理、限流、熔断、降级
![img](imgs/t11.jpg)

#### 加入服务总线
![img](imgs/t12.jpg)

#### docker管理，屏蔽环境差异，加速部署，提升运维效率，k8s
![img](imgs/t13.jpg)
![img](imgs/t14.jpg)

#### 云部署，CDN+SLB+WAF可以由云服务提供，也可以自己搭建，docker+k8s
![img](imgs/t15.jpg)



[-](https://zhuanlan.zhihu.com/p/69421196)
