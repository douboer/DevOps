
## 技术保障部数字化转型报告

History

时间 | 内容 | 作者
--- | --- | ---
2019/9/8 | 初稿 | CG
2019/9/9 | 增加不同团队数字化转型输出 | CG

---

### 技术保障部数字化转型怎么转，先弄清楚为什么和怎么做问题

转型前事务驱动或流程驱动工作，事务可能是一揽子计划，也可能是一些零散的任务，事务驱动就是完成计划或任务；流程驱动是业务流程固化，作业是在一系列的流程和规则下完成，流程驱动是原来信息化的核心内容。数字化则要求数字驱动，数字能够准确反映当前不同切面的健康状况，进而推动工作生产改善。

**数字化转型要点：**

> -	数字驱动
<br>数字化转型要从事务、流程驱动转变为数字驱动。
> -	量化、分析
<br>数据可能是海量和无序的，通过量化能掌握进度，通过分析发现问题, 进而开展精准改进。
> -	敏捷，速度
<br>数字化最终为了能够更好服务客户或服务生产，数字能反映当下，因此，数字本身就有敏捷的特点，要求组织能够快速跟进。也即敏捷型组织才能匹配数字化转型的要求。
> -	迭代，连续性
<br>事务或流程驱动大多属于计划性或外部驱动，数字却反映持续的变化，数字驱动推动快速迭代，从而持续改进，这是敏捷性组织的要求， 非敏捷组织跟不上数字化要求。 
> -	自动化
<br>自动化是数字化转型的基本要求，在自动化基础上，才具备敏捷的要求。
> -	共享、协作
<br>原来信息化下，各部门、各系统之间往往是独立的，各部分都是信息孤岛，功能也是垂直烟囱式的发展，新的项目就是一条新的烟囱，这种状况数据都是大象的一只腿，不是全貌，数字化很难实现，数字化要求数据的流动，数据是互相参照，形成画像，这样分析及结果才有价值，才能指导生产，驱动效率提升。
> -	安全
<br>数据成为生产资料，数据发挥更大价值，也承担更多风险，数据开放下的安全保障尤其重要。

**具体到运维支撑测试数字化转型工作**
- 支撑工作就是典型的事务驱动，这个事务就是故障、投诉或项目支撑工作。数字化转型有必要梳理和设立一些数字检视点，通过这些检视点数据分析，判断健康度，及早预警，早于投诉发现问题，解决问题。在数据的采集、分析由运维团队介入，引入自动化手段，甚至可以进行健康度打分。监控人员从原来主动定时查看，增加邮件、短信等推送方式的告警接受和预处理。 对于项目支撑，考虑到项目的个性化，零散化，是不是不能开展数字化转型呢？关键在于标准化基础上的数字化支撑， 标准化便于形成统一文通，统一FAQ口径，还可自动化处理，避免疲于应付客户要求，进而实现更多的远程支撑，减少现场支撑量，降低成本。

- 运维工作的数字化转型，主要要转变被动的“救火式”运维模式，这种模式出现问题后着手处理，被问题牵着鼻子走，运维人员看似忙碌，效率却不一定高，运维质量也很难提高，运维开发如果被困在这种低质量的应付事务中，就很难腾出精力从更高的层面优化系统，避免问题于未发生前，这种被动处理方式，用户满意度必定也会下降。 转变这种模式，要有一套方法论来指引，如devops，并辅之以相应的工具手段， 用拥抱变化的态度来匹配敏捷性组织的要求。 <br><br> devops敏捷和快速迭代意味着更频繁的发布和部署， 运维自动化和研运测的全流程贯通是内生要求， 此外， 响应变化和快速迭代也要求运维、测试、支撑团队成员能够快速了解和跟进项目现状， 确保测试、上线、支撑顺畅不脱节，所以devops重视Dev开发与Ops运维之间沟通合作，并需让它成为公司文化惯例，当然，沟通的形式多样，会议或面对面是一种，数字化转型更要求采用数字化手段来确保dev到ops的消息流转，就避免如修改配置运维不知悉导致部署后系统不能运行，更新的需求没有同步到测试导致新用例未覆盖新需求等问题。目前已全面使用自动化运维平台实现服务器、应用、业务的统一监控纳管，及进行环境部署、上线、监控、告警。

- 测试工作数字化，自动化测试首次成本会高于手工测试，但自动化测试的收益是随着测试次数和重复次数的增加而相应增加，此外自动化测试还存在维护工具和自动化用例编写的维护成本，数字化转型要用数据来充分分析自动化测试节约的成本情况，成果可量化，过程可量化。测试工作像来料加工厂， 工作量的峰谷特性明显， 管理上拟引入OKR法来推进团队工作， 结果产出可量化， 目标可追踪， 更好推进组织绩效 。

- 数字化甚至智能化对工具的要求也随之提高，开源社区快速发展，工具可选很多， 但工具应自主可控， 应具有开放性， 自主可控才能微创新以更好服务于业务， 工具应与业务结合才有意义， 才有比较优势。 支撑运维都应懂业务， 又懂技术。 自主可控并不是自己造轮子， 但要能够整合这些工具形成有机整体服务于业务， 而不是烟囱式的， 这不符合数字化的自动化、信息流动和敏捷的特点， 比如自动化测试大家都在用selenium，是成熟框架， 但在此基础上结合业务进行脚本封装就是降低手工过程，提供复用效率的手段， 把selenium内嵌在平台中，打通测试项目管理、测试用例管理、GUI录制并脚本化、自动化用例编写、自动化脚本的参数化、测试报告输出和统计等能力， 甚至结合postman等接口测试工具， 这些需要自己来整合。作为测试团队，要考虑要更多，比如怎么做安全测试？ 安全测试完成后如何自动化修复漏洞？ 怎么做性能测试？ 目前安全测试还独立在做， 还没有办法嵌入到自动化测试平台中， 性能测试已经能够在自动化测试平台中进行， 但总体使用还比较少， 这些部分在数字化转型中要加强。 

- 数字化转型最终是服务于客户体验的持续改进， 技术保障部不面向最终客户需求， 但不同团队输出成果的使用方便是客户， 支撑目的是解决用户使用问题， 用户问题的量化是有的，但数字化的方式的统计分析还是不够， 比如前述的跟用例的对比， 检视点数据/账单对比分析等需要加强。自动化测试平台的使用对象是自动化测试团队，自动化测试团队就需要定期提供量化的反馈给运维开发团队。 运维部署上线服务于devops，上线情况应量化的反馈给dev。
<br>

### 技术保障部数字化转型输出
<br>

功能块 | 转型要点 | 数字化输出
---- | ---- | ----
支撑 | 标准化，支撑事务形成标准化，不同阶段量化输入输出、介入方式和程度 | 安审支撑标准化文档流程
支撑 | 数字化监控,对日常监控指标进行提炼，重点指标邮件短信等方式即时通知到人 |  分等级、分类型监控指标报告
支撑 | 数字化检视点，梳理业务流程，插入检视点自动对接口数据和消费情况进行比对核查，确保一致，不一致提供告警 | 数据接口报告（如短信、审计、话单...）
支撑 | 数字化故障预防，梳理历史报障、投诉工单，采用数字化手段，变被动人工保障为主动自动巡检 | 故障历史数字化报告（包含改进点梳理）
运维 | 敏捷，工具、方法论 | 体现敏捷思维工具报告（体现工具名称、选型、作用、使用体验）
运维 | 运维服务质量数字化 | 
运维 | 高可用性指标，梳理故障点，部署HA | 单点数字化
运维 | 协助沟通，会议沟通外通过数字化手段粘合dev和ops的信息流动 | *落实动作*
运维 | 工具的共享开放程度，工具被外部使用情况 | 自动化运维、自动化测试平台使用情况报告
运维 | 自动化运维，服务器、应用、业务统一纳管，故障隔离与自愈 | 自动化运维数字化报告 （服务器、应用、业务情况报告）
运维 | 数据可视化，网络可视化 | 自动化运维数字化报告
测试 | 试行OKR | *落实动作*
测试 | 自动化用例量，自动化用例覆盖率 | 测试数字化报告 （按项目，进度、自动化覆盖率）
测试 | 全面自动化及自动化成本量化测算 | 测试数字化报告 （成本测算）
测试 | 报障投诉与测试的关联分析 | 测试数字化报告
测试 | 自动化测试工具使用对比打分反馈，推动工具改进 | 自动化测试工具、平台选型报告
测试 | 项目自动化性能测试清单、比例 | 测试数字化报告
安全 | 安全内外部工作量化，安扫及修复情况量化，分项目安全保障梳理 | 安全数字化报告
安全 | 安全工具选型研究 | 安全数字化报告
安全 | 安全自动化，安全嵌入测试中 | 安全数字化报告
<br>


