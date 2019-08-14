
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


### 实验 & 性能测试 & benchmark


### references
1. [rocketmq压测](https://www.cnblogs.com/guazi/p/6661977.html)
1. [rocketmq github](https://github.com/apache/rocketmq/tree/master/docs/cn)
1. []()
1. []()
1. []()

[0](http://www.infoq.com/cn/news/2017/02/RocketMQ-future-idea)
[1](https://www.infoq.com/articles/alibaba-apache-rocketmq)
[2](https://github.com/openmessaging/specification/blob/master/usecase.md)
[3](http://openmessaging.cloud/docs/benchmarks/)
[4](https://medium.com/@Alibaba_Cloud/rocketmq-into-the-500-000-tps-message-club-357cdde3ed2e)

