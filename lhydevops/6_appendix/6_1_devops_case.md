# DevOps案例——Etsy

## 1. 公司介绍
Etsy成立于2005年，是一个电子商务平台(C2C)，以手工艺制品买卖为主要特色，其核心理念是社区化的C2C平台经营，基于此理念网站发展出了六大功能：论坛、虚拟实验室、聊天室、小组、微件、博客。

#### 网站功能
1. 虚拟实验室：Etsy为用户设置的在线课堂，学习与社交的方式，可以与手工制品培训人员互动学习
2. 聊天室：公共聊天室，鼓励交流，增强社区黏性
3. 小组：主题群组，组织线下聚会，通过聊天室和虚拟实验室进行线上交流
4. 微件：用户插入到社交网站的标志性图标等
5. 博客：面向Etsy社区的精美手工艺杂志，艺术家介绍、新手指南、主题活动通知，内容质量非常高，吸引用户

#### 技术栈
PHP
#### 业务规模：2014年数据
1. 200多个国家的4200W用户
2. 100W活跃卖家
3. 13亿美元销售额

#### 系统规模
1. 访问量（Visit）：60W/月
2. 页面浏览量（PV）：15亿/月

#### 部署能力
每天超过60次部署

#### 开发策略：
1. 反复做许多小的、持续的变更=需要=>每天多次部署
2. 开发人员确保：是否有足够的信心来部署这个变更

#### 组织结构
1. 600员工
2. 核心团队，团队规模、角色配置
3. 核心平台团队：10~15人：整体负责服务器及系统层与应用层的接口，为上层开发特性的工程师们提供服务，如数据库接入、图片存储系统、异步任务管理等

#### 问题

1. 业务与组织规模的快速扩张带来工程与管理问题，比如构建压力大，发布堵车等

## 2. 组织与文化

### 文化

原技术总监，现任CEO $$Chad$$ $$Dickerson$$ ：  
    
1. 代码是工艺品（Code As Craft）
2. 开发和运维是目标统一的合作者（交付团队）


### 组织

每个团队规模：3~7名工程师+1名产品经理+1名设计师


### Etsy模式
#### 组织文化
##### 1. 工程师的快乐

1. 尊重工程师
2. 良好的工作环境
3. 丰盛的午餐
4. 每个人都可以部署代码（充分授权）
    
        easy deploys == developer happiness

    *本质：快速获得反馈，快速获得成就感*

5. 发布火车（排队）

##### 2. 委派运维

内容：出席开发会议，参与新特性的发布，掌握开发团队的工作情况，以便提出自己的专业意见，比如第三方接口的稳定性等，但是该运维工程师不是只为该团队服务。

目的：，

1. 让开发了解运维如何进行（专业信息的双向流通），培养开发的自运维能力
    
    *搜索团队已经能够处理日常的运维问题，当无法处理时，他们会反馈给专业的运维团队处理*

2. 运维团队会根据掌握的产品发布时间和内容预估基础设施需求，提前计划，寻求解决方案，比如服务器需求、新工具与技术的研究

    *互相了解对方的工作，理解对方的痛苦和努力，避免因为不了解而造成的误解，避免埋怨，提供正向的协作和沟通环境*

3. 打破部门墙，增强开放性的协作和交流，实现更频繁的跨组织协作和沟通
	

##### 3. 其他

1. 不要设置DevOps团队或者岗位
2. 学习型文化，不惧怕失败
3. 团队的目标统一


#### 频繁部署

#### 跟踪每次发布

#### 度量一切

#### 测试用例分组




参考

1. https://codeascraft.com/2010/02/10/code-as-craft/
2. https://codeascraft.com/2010/02/17/dev-ops-cooperation/
3. https://codeascraft.com/2011/06/06/optimizing-for-developer-happiness/
4. https://codeascraft.com/2012/02/13/the-etsy-way/
5. https://codeascraft.com/2011/02/04/how-does-etsy-manage-development-and-operations/

*多篇文章总结而成，分布于2010~2012年*

## 3. 增量构建

### 原则
主干代码一定是时刻保持可发布到产品环境的状态
### 需求
在提交前必须验证变更

### 问题

1. 在开发者VM上无法完整通过所有测试套件
2. 在集成环境，执行一次完整测试需要3小时以上，使用CI集群可以降低到30分钟
3. 在集成环境，由于失败后重新构建和修改后重新构建导致时间远超过30分钟

### 原因

1. 集成环境测试执行通过慢的原因是在集成之前，从没有真正完整执行过一次测试套件，导致集成环境测试失败率高、反复多次
2. 在提交前（开发环境VM），开发人员无法在合理（较短）的时间内完整执行一次测试套件
3. 多名开发在单台机器上执行测试套件会相互之间干扰，且影响性能

### 实践内容：
1. 基于稳定版本的增量式部署和测试（Etsy使用PHP语言，动态语言）

    使用svn diff（Git同理）和稳定版本（trunk latest）对比，并将补丁文件覆盖到持续集成环境中的稳定版本之上。该方法可以实现多人同时部署更新并进行测试，相互之间不影响（并行测试）
2. 具体方法
		1）Create a new Jenkins Freestyle Project(or copy an existing) and
			Select Parameterized Build
				File Parameter: patch.diff
				String Parameter: username
			Set up the SCM as usual
			Add an Execute Shell build step: Apply the patch.diff
			Use $username in the recipient list of the e-mail publisher
		2）Write a short bash script that
			Creates a patch
			Sends a cURL request with the patch and $USERNAME to start a build of the Jenkins job
    代码示例：

    ```
    #!/bin/bash
    
        HUDSON="ci.example.com"
        LOCATION="/home/$USER/working_copy"
        PATCH='patch.diff'
        cd $LOCATION
        svn diff > $PATCH
    
        file_param="{'name': 'patch.diff', 'file': 'file0'}"
        user_param="{'name': 'executor', 'value': '$USER'}"
        args=("$@")
        for ((i=0;i<${#args[@]};i++)); do
          curl -F file0=@$LOCATION/$PATCH 
               -F json="{'parameter': [$file_param, $user_param]}" 
               -F Submit=Build http://$HUDSON/job/try-${args[i]}/build
        done

    ```

3. 文化

    在提交之前一定要try一次，是团队自觉遵守的规范

4. 工具

    [TryLib](www.oschina.net/p/trylib) 是简单的PHP库，帮助你生成工作副本之间的差异报告，发送到Jenkins，在最新代码分支上运行测试套件。Try将Jenkins和Deployinator连接起来。

### 参考

1. Mozilla的TryServer：https://wiki.mozilla.org/ReleaseEngineering/TryServer
2. https://codeascraft.com/2011/10/11/did-you-try-it-before-you-committed/
*2011年10月*

## 4. 构建集群

### 原则

    1. test in a clone of production environment
    2. keep the build  fast 

### 背景

1. 业务与团队扩充，测试套件的执行压力增加，每天超过1950次构建与测试需要执行，如果在提高执行效率，避免拖慢交付流水线

### 问题

1. 开发者在自己的VM中执行测试，破坏了“在类生产环境进行测试”的持续集成原则，因为VM上可能存在开发自己安装的软件
2. 团队大家遵守规范和文化，不会破坏可发布的状态，采用主干开发并使用,使用Try（通过Jenkins将开发者提交的代码增量应用到具有稳定版本代码库的服务器上，并且执行所有的构建与测试）执行提交前验证，导致每天需要执行的测试套件次数增长较快（10个开发者，平均每天515次try，超过13700次测试套件的执行）

3. 不同的构建/测试任务对CPU和磁盘I/O的消耗各不相同，同时执行多个同类型的任务会导致资源瓶颈，构建服务器压力较大
4. 构建服务器上，多个构建/测试任务同时执行时，容易导致工作区内容冲突


### 需求

1. 测试套件执行时间保持在5分钟内
2. 需要根据测试的不同类型，灵活的将测试分配到不同的服务器上执行，以免造成资源的负载过高，形成卡顿
3. 工作区内容独立，即文件系统独立

### 实践

    核心策略：尽量在主干分支上开发


#### Etsy的测试主要可以分为两类：


| 类型 | 测试阶段 |量级 |说明|
| :-- | :-- | :-- |:--|
|CPU消耗型| 单元测试 | 轻量级 |对CPU的压力较大|
|I/O消耗型| 集成测试 | 重量级 |对磁盘I/O压力较大|

#### 虚拟化构建环境

1. 基于LXC的虚拟化技术，每个容器都是独立的构建/测试环境，均衡工作负载。

2. 容器和Executor的比例是1：1，每1个独立的容器都是1个slave，实现了资源隔离，避免了多个Executor访问同一个workspace目录，也更加便于使用Virtual Madness实现构建环境的自动化提供

3. 采用Divide and Consur策略和Jenkins的master project插件，实现测试套件的并发执行




#### Virtual Madness

Virtual Madness是Etsy管理容器化构建环境平台，Etsy采用LXC来实现构建环境容器化（此时还没有Docker）

注：在Etsy，构建服务器采用实体机（**刀片式服务器，每个刀片可以视为一台单独的服务器**），具体配置如下:

*2U的超微服务器，4个刀片，每个刀片挂载3块SSD，共12块盘*


##### Virtual Madness界面
其中会显示容器的运行状态，容器被挂载到哪个Jenkins上，容器所在的物理磁盘等（BOB代表容器）

![](https://codeascraft.com/wp-content/uploads/2013/09/blog1-e1379952261153.png)

*注：每一列就是一个刀片，共3块盘，每一列划分为不同的用途，如BUILDTEST01.NY4DEV即构建与测试用的服务器，在纽约*
##### 一键创建容器
Etsy坚持一键部署原则，构建环境管理也一样

1. 选择容器创建位置

    如图所示，Host下拉列表会默认选中第一个充足磁盘空间的主机，实践中，每台主机一般为14个容器（逐渐可支持更多容器）。点击**Make it**即可创建容器
    ![](https://codeascraft.com/wp-content/uploads/2013/09/blog2-e1379952393230.png)
    
    **物理磁盘的选择规则：**每个刀片的第1块最多起4个容器，第2\3块磁盘各自最多起5个容器（4+5+5=14），如此，第一块磁盘有足够的空间以支持操作系统的使用并提供基础LVM卷（包含容器的初始化配置内容，会分发到每个容器中）
2. 使用lvcreate和mkfs.ext3创建容器时创建并挂载一个空的LVM卷
3. 将基础LVM卷的内容复制到该卷中
4. 使用Chef完成容器的配置
5. 挂载到Jenkins上并分配Executor标签（使用groovy脚本实现容器和Jenkins的连接）
    ![](https://codeascraft.com/wp-content/uploads/2013/09/blog4-e1379952550551.png)

<font color=red>**规则：每块磁盘同时只能允许执行一个重量级任务**</font>

##### 容器分类：**CI HEAVY** \ **CI ANY** \ **TRY HEAVY** \ **TRY ANY**

1. 环境维度：

    1. CI环境是后台自动执行，用于构建和更完善的测试
    
    2. TRY环境是开发者使用，用于自行构建和进行测试
    
2. 任务维度：
    
    1. HEAVY任务是指重量级任务，比如集成测试，对IO要求较高

    2. ANY任务是指轻量级的任务，比如单元测试，对CPU要求较高

##### Virtual Madness其他功能
1. 容器也可以批量创建，如图所示：

    ![](https://codeascraft.com/wp-content/uploads/2013/09/blog3-e1379952479461.png)

2. 可以重建基础容器

    ![](https://codeascraft.com/wp-content/uploads/2013/09/blog5-e1379952729482.png)
3. 每个容器的IP地址也是依靠DNS反向解析查到返回NXDOMAIN（即该IP可用）后才分配给容器的。Etsy用到了nsupdate管理DNS

### 参考资料

https://codeascraft.com/2013/09/23/lxc-running-14000-tests-per-day-and-beyond-part-1/
https://codeascraft.com/2013/09/23/lxc-automating-containers-aka-virtual-madness-part-2/

*2013年9月*

## 5. 测试分组

### 原则
    Fail fast
    Fast, Reliable Tests

### 问题

每天超过25次部署，每次部署都需要执行测试



### 需求

部署耗时需要保持在20分钟内，长时间的部署过程会导致部署队列拥堵，降低效率，也会打击部署积极性


### 实践

**主干测试**（trunk tests）：部署之前必须执行的测试，用于测试Etsy的产品功能，Etsy拥有7000个主干测试（持续增长中，并非都是单元测试，并非所有测试都要在部署前执行）

**将重量级测试套件根据相似性拆分为多个轻量级的测试套件**



#### 5分钟、11分钟、20分钟

如果主干测试失败，部署将会暂停，工程师一般将会在5分钟内解决该问题，然后重新执行测试，通过之后本次部署成功结束，考虑失败的情况，自动化主干测试必须在11分钟内完成，才有足够的剩余时间重新测试，以免部署超过20分钟太多

#### 测试执行策略
从前到后顺序执行完所有的主干测试（大于7000）需要耗时超过30分钟，如何实现11分钟：

    1. 对测试进行分组，选择性执行
    2. 将测试分发到10台Jenkins构建服务器上并行执行

**测试的执行场景**

1. 每次提交时执行
2. 点击测试按钮时执行
3. 点击发布按钮时执行

#### 测试分类


##### 单元测试（Unit Tests）

单元测试只针对一个类，无需与数据库、文件或其他基础设施的交互。Etsy拥有超过4500个单元测试，且必须在部署前执行，耗时1分钟

##### 集成测试（Integration Tests）

集成测试需要与基础设施交互，如数据库、消息队列、缓存服务等，Etsy使用PHPUnit连接DBUnit（模拟数据库服务），Etsy的[PHPUnit扩展](https://github.com/etsy/phpunit-extensions)

在Etsy的测试套件中，集成测试最慢，如果顺序执行需要耗时20分钟，**并行执行则只需耗时8分钟**

##### 网络测试（Network Tests）

部分集成测试也需要访问网络资源，如使用第三方服务发送邮件等,Etsy建议尽量避免需要依赖网络访问的测试

##### 冒烟测试（Smoke Tests）

冒烟测试是系统级别的测试，测试目标是部署完成系统，通过PHPUnit执行Curl命令，并且使用断言比对返回结果的header和其他数据

##### 功能测试（Functional Tests）

类似冒烟测试，基于GUI驱动的端到端功能测试的测试目标也是部署在测试环境的系统，Etsy使用Cucumber和Selenium进行功能测试，基于Xvfb的虚拟桌面环境驱动Firefox进行测试

功能测试脚本需要在开发和维护上投入较大工作量，在Etsy，端到端的功能测试只用于最重要的关键功能。在单元测试、集成测试、冒烟测试之后，功能测试只作为最终的验证


*编者注：功能测试对重要功能的验证是很有意义的，从用户操作的角度进行验证。比如Dropbox有一次部署将用户验证功能关闭了，导致极大的安全问题，类似这样的关键功能应该增加最后一道门槛。*

#### 不稳定测试（Intermittent Tests）
不稳定测试：偶尔会失败的测试，但是对于开发很有帮助，此类测试不能纳入主干测试，因此Etsy建立了PHPUnit中的flaky组，当开发者认为测试不够稳定时，可以将其划分到flaky组中，并在其他场景下使用

*零容忍对待不稳定测试*

#### 慢测试（Slow Tests）

符合80/20原则，少数测试占用了主要的测试执行时间，工程师会将耗时长的测试划分到slow组，失败和取消最慢的20个慢测试，测试套件执行时间会有明显提升，此类测试依然会在某些场景下执行，但是主干测试中不进行

#### 睡眠测试和时间测试（Sleep Tests and Time Tests）

好的测试不会使用sleep()，也不会依赖于系统时间。
追求测试覆盖率会导致出现低质量的测试用例，尤其是维护历史系统时，Etsy允许这类测试存在，但是不在部署前执行这些测试

### 工具
1. PHPUnit，使用其他@group的注释功能，从逻辑上将测试划分为多个子集。
2. Jenkins，使用XUnit插件，选择性执行测试
    
    ```
    <groups>
      <include>
        <group>dbunit</group>
      </include>
      <exclude>
        <group>database</group>
        <group>network</group>
        <group>flaky</group>
        <group>sleep</group>
        <group>slow</group>
      </exclude>
    </groups>
  ```
  *解释：PHPUnit任务只会执行dbunit，不会执行database,network, flaky, sleep,slow；所有单元测试必须被执行。*  

### 总结
1. 识别并分组执行测试
2. 并行执行测试
3. 只保留对部署对重要的测试

##### 文化

Etsy的部署由工程师管理，而非运维或者其他发布管理团队
理由：你写的代码，你自己发布到线上。$$Even $$ $$dogs $$ $$deploy $$ $$code$$

授权工程师对测试用例进行分类

### 参考
https://codeascraft.com/2011/04/20/divide-and-concur/

*2011年4月*
