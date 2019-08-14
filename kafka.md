
# 消息系统

### kafka

:question:
- 异步
- 解耦
- 顺序
- 削峰填谷


kafka是个日志处理缓冲组件，在大数据信息处理中使用。和传统的消息队列相比较简化了队列结构和功能，以流形式处理存储（持久化）消息（主要是日志）。日志数据量巨大，处理组件一般会处理不过来，所以作为缓冲曾的kafka，支持巨大吞吐量。为了防止信息都是，其消息被消防后不直接丢弃，要多存储一段时间，等过期时间过了才丢弃。这是mq和redis不能具备的。
kafka通过zookeeper来存储集群的meta信息



### rocketMQ

![img](imgs/rocketmq.png)
![img](imgs/rocketmq.jpeg)

心跳机制
- 自带name service，脱离zookeeper，自动Master选举
- broke与所有nameSVR保持心跳请求，30s间隔，2min无心跳，nameSVR判定broke下线，调整topic与broke关系
- Consumer跟Broker是长连接，会每隔30秒发心跳信息到Broker。
  Broker端每10秒检查一次当前存活的Consumer，若发现某个Consumer 2分钟内没有心跳， 就断开与该Consumer的连接，并且向该消费组的其他实例发送通知，触发该消费者集群的负载均衡(rebalance)。
- producter每30秒从Namesrv获取Topic跟Broker的映射关系，更新到本地内存中。
  再跟Topic涉及的所有Broker建立长连接，每隔30秒发一次心跳。 
  在Broker端也会每10秒扫描一次当前注册的Producer，如果发现某个Producer超过2分钟都没有发心跳，则断开连接



### 实验 & 性能测试 & benchmark


### references
1. [rocketmq压测](https://www.cnblogs.com/guazi/p/6661977.html)
1. [rocketmq github](https://github.com/apache/rocketmq/tree/master/docs/cn)
1. [](https://blog.csdn.net/javahongxi/article/details/84931747)
1. [](https://blog.csdn.net/zshake/article/details/77824020)
1. []()

[](https://www.infoq.cn/article/2017/02/RocketMQ-future-idea)
[](https://www.infoq.cn/article/IlP-Jk87KLyw63uDfNA8)



