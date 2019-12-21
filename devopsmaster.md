# devops master certificate

--- 
1. 验收测试的最佳选择? Happy Path
2. 创建可执行文件的工具是一种什么样的构建工具? Make, 面向产品
3. 一出问题就骂外包: 加强协作, 不指责.
4. 告诉老板Devops能带来哪些效果: 快速发布, 降低成本, 直接支持业务产出
5. DevOps开始时要做什么? 愿景, 目标.
6. Devops团队的成员? 6-8人, Cross function 跨职能
7. 紧急变更打补丁? RFC 申请变更, 分析影响, 通知利益相关方
8. 云计算的哪个特性能实现自动部署? 标准栈
9. 云的哪个特性不让人放心想上云? 安全, 服务级别(SLA)
10. 哪个不是实现良好配置管理的策略?不能把二进制放到配置管理中
11. 什么是管理基础设施的原则? 原则是后面个自动化, 版本控制, 监控
12. 什么是构建依赖, 什么是运行依赖? 编译是构建依赖
13. 手动软件发布过程的优点? 加强协作, 加强Review
14. 什么不是部署管道的一部分?
15. 一个新版本每三个月发布一次是Devops实践? 迭代中要进行增量发布
16. 为什么SLA对客户如此重要?  对客户有价值
17. 发生故障是基础设施重建? 自动化提供自动化运维
18. SOR? 协作型
19. 向其他同事抱怨不直接发生冲突? 避免/回避
20. DevOps Mindset?  非谴责, 高效, 亲和
21. 什么是协作? 多人根据输入达成共同的输出
22. 什么是亲和? 不同群体
23. 如何使Devops更加成熟? 戴明环, KAIZEN, 可视化控制和可视化管理.
24. Devops文化转变包含什么? 新和, 协和, 高度信任, 同理心, 不谴责, 单件流
25. 项目在DevOps中取得成功必须改变什么? Mindset,  千万不要选工具
26. 重复可靠是指什么过程? Release
27. Devops反模式? 手工发布, 开发完后才部署
28. 迭代时间和频次取决于什么? 业务需求
29. 持续部署的优点? 性能和一致性不相冲突
30. Obeya作战系统? 共享信息, 快速决策
31. CI的好处? 更少的Bug, 更低的成本, 更快发现Bug
32. 既能保证质量又能提高发布效率?单件流
33. 构建失败时应该怎么解决? 谁提交失败谁负责修复o

---
DevOps白皮书
第1部分:A journey to DevOps The DevOps framework should support business outcomes directly。 

第2部分:What is DevOps for the enterprise system? DevOps can also enable maturity by using W.E. Deming’s Plan Do-Check-Act cycle.

第4部分DevOps Body of Knowledge:第四节TPS (Lean) concept as foundation :Building a stream-lined supply chain of IT services is difficult because there are many  items and it is necessary to change your mindset from the familiar existing development cycle and its methodologies.(JIT means building up a stream-lined supply chain with one-piece 
flow.) 

第4部分 DevOps Body of Knowledge:IT service management Service on just providing quick and frequent IT services and reliable operation and is led by the service  master. It is most suited for SoE and SoR continuity is an essential part of the warranty (fitness for purpose) of a service. If service  continuity cannot be maintained and/or restored in accordance with the requirements of the business, then the business will not experience the value that has been promised. Without continuity, the utility (fitness for use) of the service cannot be accessed.

第 5 章角色职责: Leads the team and facilitates, this role is the same as “Scrum Master” in Scrum.Implements visual control across the entire process and has a strong focus on establishing a stream-lined process with one-piece flow.

第5部分:DevOps Team Roles (Leads the team and facilitates, this role is the same as “Scrum Master” in Scrum. Implements visual control across the entire process and has a strong focus on establishing a stream-lined process with one-piece flow.) 

第5部分:Gatekeeper / Release coordinator: Responsible for  monitoring the operational status and progress of the next release of the IT service. Make go/no go decisions about deployment according to criteria including security, compliance, regulatory requirements, maturity of operation team and their process views.

第7部分:DevOps Process Project Planning The service master creates the vision, goal, and value of the project, and then puts together the DevOps team members. 

第 7 章 JKK 解释：它基于 100％完成高质量项目创建完成定义

第7部分:DevOps Process Obeya is a war room which serves two purposes - information management and on-the-spot decision making.

第8部分 DevOps implementation Collaboration: (Standard): This focuses on just providing quick and frequent IT services and reliable operation and is led by the service  master. It is most suited for SoE and SoR 

DEVOPS团队由 6-8 名成员组成的跨职能团队。

The Service Master EOL

精益管理中的八大浪费类型

持续交付第11章基础设施和环境管理 225页：自动化的准备工作与自动化维护相结合，可保证出现问题就能在可预见的时间内重建基础设施。

持续交付第11章 11.7.2章节 虚拟环境和部署流水线。250页 构建和发布管理系统应该能记住用来运行部署流水线的虚拟机模板，当部署到生产环境时，也应该能够启动同一套虚拟机模板。

持续交付第四章 测试策略的实现 71页当你有时间写更多的自动化测试时，很难在Happy Path和Sad Path之间进行选择。 如果你的应用程序比较稳定，那么Happy Path应该是你的首选，因为它们是用户所定义的场景。

持续交付第4.3章节 75页制定遵守INVEST原则[即独立的（Independent）、可协商的（Negotiable）、有价 值的（Valuable）、可估计的（Estimable）、小的（Small）且可测试的（Testable）] 的用户故事[ddVMFH]及考虑其验收条件。

持续交付第15章 持续交付管理：340页企业治理更关注于符合度 （conformance），即遵从性、保障、监管、责任和透明管理， 而业务治理（business governance）更关注业务和价值创造的执行度（performance）。其实，执行度和符 合度都可以满足。这一道理在持续交付中也是正确的。通过确保交付团队能得到应用 程序在类生产环境上的不断反馈， 是部署流水线达成“执行度”这个目标的方法和手段。部署流水线使交付流程更加透明，来帮助团队达成符合度

持续交付 5.4 提交阶段 97页

15.3章节 344页：我们的关注点在于迭代和增量交付，以及跨功能职责角色之间的协 作。345页：Scrum是一种迭代式增量软件开发过程，通常用于敏捷软件开发。包括一系列 实践和预定义角色的过程框架。347页 开发与发布：我们推荐以迭代增量式过程进行软件 的开发与发布。

第3章 持续集成 44页 高效使用持续集成 的那些团队能够比那些没有使用它的团队更 快地交付软件，且缺陷更少。在交付过程 中，缺陷被发现得越早，修复它的成本就越低， 因此也就大大节省了成本和时间。因 此我们认为，对于专业的软件交付团队来说，持续集成与版本控制同等重要。

持续交付 3.7 章节 60 页从技术角度上看，最为简单的方法（也是从流程角度上讲最有效的方法）就是使 用共享的版本控制系统和持续集成系统。 63 页 3.8 章节：，DVCS 引入了一个中间层：在本地工作区的修改必须先提交到本地库，然后才能 推送到其他仓库，而更新本地工作区时，必须先从其他仓库中将代码更新到本地库。以及 14.4 章节

持续交付第五章。什么不是部署管道的一部分？88页

6.2 章节 构建工具：117 页 各构建工具的不同点在于它是任务导向的，还是产品导向的。任务导向的 构建工具（比如 Ant、NAnt 和 MSBuild）会依据一系列的任务描述依赖网络， 而产品导 向的工具，比如 Make（创建可执行文件），是根据它们生成的产物（比如一个可执行文件）来描述。

项目失败：转向持续部署模式的最佳第一步是什么？开发应非正式地涉及整个项目的运维，并合作共同创建部署脚本。

哪种做法有助于在不影响质量的情况下提高速度？One-piece-flow

手动软件发布过程的优点是什么？鼓励协作，团队成员则审查彼此的工作。

第八章：自动化验收测试 154 页：首先，由于反馈环将 大大缩短，缺陷被发现得更快，也就更容易修复。其次，由于测试人员、开发人员和 客户需要紧密合作才能创建一个良好的自动化测试套件，这会促进他们之间的良好合 作，而且每个人都将关注软件应该交付的业务价值。

第 3 章，3.5.1 52 页、53 页  您的同事说：“即使构建中断，您也应该Check In。

老板问实施DevOps，What would not be a good reason? 团队解释了新实践在另一家公司中的运作方式。

8.5.1 验收测试中的状态 p167首先，要抵制使用生产数据的备份作为验收测试的测试数据库的诱惑（尽管有时 它对吞吐量测试是有用的）。相反，我们要维护一个受控的数据最小集。测试的一个关 键方面是建立一个确知的起始点。通过生产数据的副本以进行测试。

12.4 章节 数据库回滚和无停机发布 P268

11.9 基础设施和应用程序的监控 p257 收集数据、记录日志、建立信息展示板、行为驱动监控。提出了四种可能的操作来排除应用程序故障 1,2&4

13.5.5 循环依赖。 P302 循环依赖构建阶梯

13.3 依赖 P286 构建时依赖与运行时依赖之间的区别如下：构建时依赖会出现在应用程序编译和链接时（如果需要编译和链接的话）；而运行时依赖会出现在应用程序运行并完成它的某些操作时。

第 2 章 配置管理 P24 进行增量更改，满足我所在组织的所有合规性规定

第 11 章 基础设施管理 P224  第 11 章 基础设施管理 P224
准备部署环境的过程以及部署之后对环境的管理是本章的主要内容。然而为了能 够做到这一点，就要基于下面这些原则，用一个整体方法来管理所有基础设施。 ①   使用保存于版本控制库中的配置信息来指定基础设施所处的状态。  基础设施应该具有自治特性，即它应该自动地将自己设定为所需状态。  通过测试设备和监控手段，应该每时每刻都能掌握基础设施的实时状况。 什么不是管理基础设施的原则？编写新的通用基础管理脚本。

2.2 章版本控制 P27  什么不被认为是实现配置管理这一目标的有效策略？始终将二进制文件和配置信息保存在一起。

11.8.1 P254  Cloud 安全和服务水平

11.8.2 云中平台 P255 将应用部署到完全标准化的应用栈上，就意味着不需要担心测试环境、试运行 环境和生产环境的配置和维护，也不需要担心虚拟机映像的管理。最后一点尤其是革命性的。在本书中，用了大量的篇幅来讨论如何自动化你的部 署、测试和发布流程，以及如何搭建和管理测试和部署环境。云中的哪个平台特性最能实现自动部署？ Standardized stack

10.5 紧急修复 P216  任何情况下，都不能破坏流程。紧急修复版本 也要走同样的构建、部署、测试和发布流程，与其他代码变更没什么区别。发布 RFC 作为紧急补丁并通知所有利益相关者。 然后根据 SLA 应用紧急补丁。P216

---
高效的 DevOps 文化需要具备：高效沟通，共识与信任，人性化的员工配置和资源
写一份项目章程很重要，一起写项目范围最好的理由是什么：确保所有团队对成功有着相同的定义
衡量已找到程序错误的总数是跟踪项目质量最好的方法吗：全局范围内而非局部进行优化
服务级别协议对专注于増加商业价值有所帮助

---
1. 场景：5 个月 h 后……，开发完成后才向类生产环境部署（考点，反模式）
2. 在发布流程为软件发布创建一个可重复且可靠的过程。（考点，软件交付原则）
3. DEVOPS 应该建立一个 Pull System、One Piece Flow 的 IT Super Chain
4. 建立 DEVOPS New Mind of All People，流程 One Piece Flow
5. 场景：一家公司由于供应商的要求，只剩下 5 个月的时间建立 DEVOPS 的团队，他 们如何决定他们的迭代时间和频次？ 根据符合业务要求来确定
6. DEVOPS 四个支柱 Collaboration，Multiple People
7. 要进行 DEVOPS 转型，Coach Team 中的每一个人，建立 Blameless 的文化 
8. DevOps 转型：沟通、同理心、人员和资源
9. 场景：CEO 以前总是骂下面的人，现在采用了 DEVOPS 方式，情况有所好转，但是 没有达到理想效果，应该：Trust each Other，建立 Blameless 文化
10. 一个人抱怨另一个人，通过邮件到处宣扬对另一个人的不满，Avoidance
11. Gatekeeper 的职责：Security、Compliance、Regulatory Requirements
12. 浪费的类型：Extra Feature
13. 在 DEVOPS 项目计划时，SLR 包含那些内容、安全、连续性等内容
14. DEVOPS 项目开始时要做那些工作？Vision、Goal 等
15. SOR 适用月那种 DEVOPS 方式，Collaboration
16. Obeya，信息共享，做决定
17. Auto Provisioning  Auto maintenance
18. VM 模板
19. SLA 的重要性，业务连续性
20. 在稳定没有时间的情况下进行：Happy Path 测试
21. 场景：销售人员提出了一些列销售问题，这个用户故事符合 INVEST 原则？问选哪 一个：可测试性
22. Development Pipeline 对治理的作用
23. 提交阶段需要做什么工作？
24. 一个团队三个月进行一次新版本的部署，而且是按照模块开发和部署，因此他们认 为他们的采用的是 DEVOPS 的方法，选项问适和否
25. 持续集成的优势 fewer bug、cheaper
26. Check In polices
27. Run time Build time
28. 安全问题出现后，如何进行紧急变更
29. 谁可以决定服务终止
30. 数据库管理，此题是技术题，大概内容是要做一个回退脚本，且要保证原有数据不 能删除，但可能重构表内容。
31. 不上云的理由，安全，SLA
32. Standardized stack
33. 手工发布软件的优势
34. 手工测试的类型
35. 场景：某人要提交有问题的代码，且振振有词讲到提交后可能通过变更进行更正。 
36. 循环依赖
37. Ensures performance (fast delivery) and conformance (to requirements
38. 不要将生产数据库拿到测试环境
39. JKK 100%质量覆盖
40. 版本控制，巴黎，伦敦，悉尼，还有其他地方存在时差，如何进行版本控制
41. 基础架构环境准备
42. Cross Function 的 6-8 人
43. 不要把二进制文件放进构件库中
44. Make such as an Executable
45. Product Oriented
46. Process Master 的职责，建立可视化看板，单件流等 
47. 配置管理策略，增量，合规
48. Increase speed without compromising quality
