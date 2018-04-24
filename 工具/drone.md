# drone持续集成
#### 参考文档http://docs.drone.io/
## 一、drone简介
drone引入pipline的概念，整个build过程由多个stage组成，每一个stage都是docker。

    各stage间可以通过共享宿主机的磁盘目录, 实现build阶段的数据共享和缓存基础数据, 实现加速下次build的目标
    各stage也可以共享宿主机的docker环境，实现共享宿主机的docker image, 不用每次build都重新拉取base image，减少build时间
    可以并发运行。多个build可以并发运行，单机并发数量由服务器cpu数决定。 由开发者负责打包image和流程控制。Docker-in-docker,这一点非常重要，一切都在掌握之中。相比jenkins的好处是，所有的image都是开发者提供，不需要运维参与在CI服务器上部署各种语言编译需要的环境。
    是DevOps的最佳实践！

## 二、使用drone构建
在 Drone 中，构建环境、插件以及服务容器都是 Docker 镜像。在 Yaml 中使用 image 来指定使用的镜像。<br>
