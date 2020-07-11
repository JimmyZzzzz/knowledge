# CI/CD - 持续集成与持续部署

当下 CI/CD 工具众多，有开源的也有 Online 的，有的复杂但功能强大(Jenkins)，有的虽然简单却也五脏俱全。

功能强大（大而全），可能也意味着更高的学习使用成本。
另外新出的很多 CI/CD 是完全 GitOps 的，算是小而美，使用简单，但是某些功能可能就无法通过它们实现（比如定时任务、手动指定参数进行构建等）。

可以考虑使用一个功能强大的 CI/CD 工具 hold 住全场，也可以组合一些小而美的 CI/CD 工具实现需求。
想知道具体要应该选择哪些 CI/CD 工具，就需要先分析清楚自己的需求，以及各工具都提供了什么东西给我们。


## CI/CD 功能对比

### 1. Jenkins

Jenkins 无疑是目前市面上最强大的 CI/CD 工具，可以 hold 住绝大部分的 CI/CD 使用场景。

它使用 Jenkins Pipeline 编写任务流程，有众多插件支持各类 CI/CD 功能。

每个任务都提供多种构建方式：

1. 手动设定参数，启动构建。
2. 定时使用默认参数构建，可用于各类定时任务。
3. 通过 webhook 等方式启动构建，常用于让 Git 操作自动触发构建。
4. 通过 http api 启动构建，适合于 python 等编程使用。

可以使用 Jenkins+Python 代码，打造出一个自动化运维平台。包含：

1. 前后端代码的 CI/CD
2. 自动化测试平台，通过定时任务进行自动化测试，使用 ningx/ftp 仓库进行测试记录的保存与查看，通过邮件通知或钉钉插件实现告警，。
3. CMDB 配置管理系统 资产管理系统：提供数据定时清理、服务器维护、k8s集群维护、其他资源维护等等 CMDB 功能。
   1. 比如通过 Jenkins 调用 ansible/terraform/kubeadm 等工具，进行服务器/云资源/kubernetes集群的维护。

但是 Jenkins 也存在很多问题，详见 [Jenkins Notes](jenkins/README.md)

因为 Jenkins 本身的这些问题，我目前正在寻找替代方案——能不能用多个工具来实现上述的所有功能。


### 2. Gitlab-CI

Gitlab 去年相比 Jenkins 还有很多欠缺，今年（2020）加入了多项新功能，也许有希望替换掉 Jenkins：

1. Multi-project pipelines(仅付费版): 同一个 Git 仓库可以有多个独立的 Pielines
2. Parent-Child Pipelines：可以实现层次化的 CI/CD

另外 Gitlab-CI 和 Gitlab 无缝融合，CI/CD 很方便。

Gitlab-CI 也支持定时任务、通过 API 运行 Pipeline（可自定义参数）等功能。原生支持通过邮件发送通知。

和 Jenkins 区别比较大的地方，是它没有「视图-文件夹-任务」这样的层次结构，所有的 Pipeline 其实都是附属于一个 Git 仓库的。

这样的话一些批量构建的任务，可能只能附在运维代码仓库上。尚不清楚这种组织结构合不合适。