## devops笔记

#### LB

阿里服务

```
                   redis/oss/
                   monitor/log        dataV
                 |                 |
APP - CDN - WAF -|- SLB - ECS集群 -|- RDS集群
                 |                 |
```

CDN:
<li>内容分发、复制、cache
<li>智能DNS，优化到达缓存/复制点
<li>缺点：能容可能不同步，可闲时同步

WAF价格高出SLB好多
