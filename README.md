# Everything I Know

>个人知识库，并不是教程，也不保证正确！

主要内容：

1. 用于容器化部署常见应用的 docker-compose 配置（单机）。
2. Kubernetes 生态：部署、配置、组件及使用笔记。
3. Telemetry：监控、日志、链路追踪（学习中...）
4. 容器：Docker、容器镜像仓库、Podman 等。
5. CI/CD：Jenkins/GitLabCI/ArgoWorkflow 等
6. 网络：Kubernetes 集群网络、Linux 网络（学习中）
7. 操作系统：Linux 系统、KVM 虚拟化等。
8. 编程语言学习笔记：Python/Golang/Java
9. DevOps 实用脚本
10. 研发运维一体化平台：CI+CD+SRE
11. Homelab: 家庭服务器相关，以及一些个人爱好。
12. 数学笔记：线代、数学物理方法等
13. AI 学习笔记（貌似还没开始...）
14. 信号与系统/数字信号处理（皮毛都还没学到...）

## 工具选型

随手甩出一张 CNCF 蓝图：[CNCF Cloud Native Interactive Landscape](https://landscape.cncf.io/)

## 应用部署

此仓库包含的软件，主要提供了如下几种部署方法

- docker-compose 部署：可以参考 [awesome-compose](https://github.com/docker/awesome-compose)
  - 对于使用 docker-compose 部署的单机应用，我倾向于使用 bind 文件夹绑定的方式来持久化数据。详见 [Docker 数据卷](/container/docker/Docker%20数据卷.md)
- kubernetes 部署：可以在各软件的官方文档或者官方 Github 寻找。
  - kubernetes 主流的部署方法：首推 helm，其次是 yaml 文件直接部署或者 kustomize.
  - 工作中接触到的主要都是无状态应用，对 kubernetes 数据卷的了解目前还很欠缺。


## 国内主流镜像站

由于众所周知的原因，很多时候我们需要为各种系统、应用、包管理器设置镜像源以加速下载。

主要有如下几个镜像站：

1. [阿里云开源镜像站](https://developer.aliyun.com/mirror/): 个人感觉是国内下载速度最快的一个镜像源。
    - 提供了 ubuntu/debian/centos/alpine，以及 pypi/goproxy 等主流 OS/PL 的镜像源。比较全。
2. [清华开源镜像源](https://mirrors.tuna.tsinghua.edu.cn/): 非常全，更新也很及时。
    - 但是速度比不上阿里云，而且有时会停机维护。。
1. [北京外国语大学镜像站](https://mirrors.bfsu.edu.cn): 清华镜像的姊妹站，因为目前用的人少，感觉速度比清华源快很多。
3. [中科大开源镜像源](http://mirrors.ustc.edu.cn/): 这个也很全，更新也很快。但是不够稳定。
    - 比清华源要快一点，但是停机维护的频率更高。而且前端时间因为经费问题还将 pypi 源下线了。
4. [腾讯镜像源](https://mirrors.cloud.tencent.com/): 才推出没多久的镜像源，还没用过。

首推阿里云镜像源，稳定可靠速度快。


## DevOps 资料

系统化的文档：

- [devops-exercises](https://github.com/bregman-arie/devops-exercises)
- [test-your-sysadmin-skills](https://github.com/trimstray/test-your-sysadmin-skills)
- [sdn-handbook](https://github.com/feiskyer/sdn-handbook)
- [docker_practice](https://github.com/yeasy/docker_practice)

文章集锦：

- [StabilityGuide - 打造国内稳定性领域知识库](https://github.com/StabilityMan/StabilityGuide)
- [awesome-scalability](https://github.com/binhnguyennus/awesome-scalability)
- [awesome-sre](https://github.com/dastergon/awesome-sre)
- [阿里云容器服务 - DevOps 收藏夹](https://github.com/AliyunContainerService/DevOps)

