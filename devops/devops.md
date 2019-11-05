**一句话概括：**

DevOps：研发运维一体化

DevOps（英文Development和Operations的组合）是一组过程、方法与系统的统称，用于促进开发（应用程序/软件工程）、技术运营和质量保障（QA）部门之间的沟通、协作与整合。它的出现是由于软件行业日益清晰地认识到：为了按时交付软件产品和服务，开发和运营工作必须紧密合作



**DevOps对应用程序发布的影响**

在很多企业中，应用程序发布是一项涉及多个团队、压力很大、风险很高的活动。然而在具备DevOps能力的组织中，应用程序发布的风险很低，原因如下 [2] ：

**（1）减少变更范围**

与传统的瀑布模式模型相比，采用敏捷或迭代式开发意味着更频繁的发布、每次发布包含的变化更少。由于部署经常进行，因此每次部署不会对生产系统造成巨大影响，应用程序会以平滑的速率逐渐生长。

**（2）加强发布协调**

靠强有力的发布协调人来弥合开发与运营之间的技能鸿沟和沟通鸿沟；采用电子数据表、电子数据表、电话会议和企业门户（wiki、sharepoint）等协作工具来确保所有相关人员理解变更的内容并全力合作。

**（3）自动化**

强大的部署自动化手段确保部署任务的可重复性、减少部署出错的可能性。



**实现DevOps需要什么？**

**硬性要求：工具上的准备**

上文提到了工具链的打通，那么工具自然就需要做好准备。现将工具类型及对应的不完全列举整理如下：

代码管理（SCM）：**GitHub**、GitLab、BitBucket、SubVersion

构建工具：**Ant**、Gradle、**maven**

自动部署：Capistrano、CodeDeploy

持续集成（CI）：Bamboo、Hudson、Jenkins

配置管理：Ansible、Chef、Puppet、SaltStack、ScriptRock GuardRail

容器：**Docker**、LXC、第三方厂商如AWS

编排：Kubernetes、Core、Apache Mesos、DC/OS

服务注册与发现：**Zookeeper**、etcd、Consul

脚本语言：python、ruby、shell

日志管理：ELK、Logentries

系统监控：Datadog、Graphite、Icinga、Nagios

性能监控：AppDynamics、New Relic、Splunk

压力测试：JMeter、Blaze Meter、loader.io

预警：PagerDuty、pingdom、厂商自带如AWS SNS

HTTP加速器：Varnish

消息总线：ActiveMQ、SQS

应用服务器：Tomcat、JBoss

Web服务器：Apache、Nginx、IIS

数据库：MySQL、Oracle、PostgreSQL等关系型数据库；cassandra、mongoDB、redis等NoSQL数据库

项目管理（PM）：Jira、Asana、Taiga、Trello、Basecamp、Pivotal Tracker

在工具的选择上，需要结合公司业务需求和技术团队情况而定。（注：更多关于工具的详细介绍可以参见此文：51 Best DevOps Tools for #DevOps Engineers）