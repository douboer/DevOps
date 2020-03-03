
# devops master summary

- 是什么？文化？
- devops实践？
- devops工具？
- 价值流具体化、可视化？
- 需求拆分技术？
- BA QA/Tester Dev - BDD技术？
- 谁决定能不能上线？


# 要点
1. DevOps Mindset? 非谴责, 高效, 亲和
1. Devops文化转变包含? 亲和, 协作, 信任, 同理心, 不谴责, 单件流   **Trust each Other，Blameless**
1. DevOps方法论: PDCA，KAIZEN，可视化控制&管理（obeya作战室：共享信息, 快速决策）
1. 聚焦软件交付的业务价值
1. 创建一个拉式部署流水线
1. 质量内建 + 面向上游（从Ops到Dev） + 人人对质量负责
1. 部署脚本：使用同样的部署脚本在不同环境中部署，确保部署流程幂等性
1. 尽早发现问题(编译错误，测试失败，环境问题让提交失败) fail fast fail cheap
1. 任何情况下，都不能破坏流程。紧急修复版本也要走 构建/部署/测试/发布的流程，与变更没区别
1. 发布：AB发布，金丝雀发布
1. 紧急修复 or 回滚
1. 基础设施重建：Auto provisioning - auto maintainance
1. 创建类生产环境，环境配置变更应能够触发流水线
   确保交付团队能得到应用程序在类生产环境上的不断反馈
1. 创建监控策略：collect, store, dashboard, log, monitor
1. 企业治理：
    - 符合度(conformance)，合规性，关注遵从性，保障，监管，责任，透明管理
    - 执行度(performance)，绩效，关注业务和价值
1. 验收测试的最佳路径happy path
1. 交付过程中，缺陷被发现得越早，修复它的成本就越低 fail fast
1. 拉灯

紧急变更不应该成为不走变更流程的理由

#### 精益8大浪费 DOWNTIME

type | description
-- | -- 
defect | 工序、稳定性，不合格，缺陷 => poka-yake
overproduction | 可视化，拉动生产
waiting | 
non-utilized people | kaizen，学习型组织
transportation | 单件流
inventory | 可视化，拉动生产
motion
extra processing/feature | 镀金 => 5why

#### 需求/用户故事原则 INVEST

type | x
-- | -- 
独立的（Independent） | 解耦
便于沟通（Negotiable） | 减少与客户等相关方的沟通成本
有价值的（Valuable） | 对客户有价值
可估计的（Estimable） | 开发者便于估计工作量
小的（Small） | 短小有代表性，敏捷迭代
可测试的（Testable） | 用户故事已完成的标准，或者说能够确认已完成


### references
- [写给新人的BA工作说明书](https://www.jianshu.com/p/9efbf1233a7e)
- [DevOps实施：从敏捷文化与配置文件的困惑说起](https://blog.csdn.net/enweitech/article/details/78595263)

