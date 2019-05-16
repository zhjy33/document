# docker与portainer

## 1.什么是docker
### 1）传统虚拟机技术是虚拟出一套硬件后，在其上运行一个完整操作系统，在该系统上再运行所需应用进程；而容器内的应用进程直接运行于宿主的内核，容器内没有自己的内核，而且也没有进行硬件虚拟。因此容器要比传统虚拟机更为轻便。

### 2）基本概念
docker拉取国内镜像docker pull registry.docker-cn.com/library/ubuntu:16.04


	镜像：相当于java中的类
		镜像不包含任何动态数据，其内容在构建之后也不会被改变。镜像构建时，会一层层构建，前一层是后一层的基础。每一层构建完就不会再发生改变，后一层上的任何改变只发生在自己这一层。比如，删除前一层文件的操作，实际不是真的删除前一层的文件，而是仅在当前层标记为该文件已删除。
	
	容器：相当于java的对象，是类的一个实例。创建容器时，是以镜像为基础在其上创建一个当前容器的存储层，我们可以称这个为容器运行时读写而准备的存储层为容器存储层。该存储层与容器生命周期相同
	service(swarm模式下):在服务中可以同时启动多个容器，相当于一个应用
由于docker不同于虚拟机，可以直接操作宿主机器。所以可以使用docker的volumn（卷）进行持久化操作。即可以使用容器运行数据库。
	CMD命令和ENTRYPOINT命令的区别：
	在构建容器时，会执行CMD中的命令。而且使用docker run 镜像 + 参数，启动容器时镜像名后面的命令会替换掉CMD的命令。而使用ENTRYPOINT则则会将参数传给CMD命令


## 2.什么是portainer
portainer用于管理docker及dockerswarm的可视化工具<br>
portainer搭建<br>
[root@ linuxidc /]# docker pull portainer/portainer(国内仓库地址：registry.docker-cn.com)
Using default tag: latest
latest: Pulling from portainer/portainer
d1e017099d17: Pull complete
ba5495c717cb: Pull complete
Digest: sha256:8146a5aae1135a0ccee424488c6867b438be21d1e915903a858d12e8382b817b
Status: Downloaded newer image for portainer/portainer:latest
2.2单机运行

    如果仅有一个docker宿主机，则可使用单机版运行，Portainer单机版运行十分简单，只需要一条语句即可启动容器，来管理该机器上的docker镜像、容器等数据。

创建数据卷：

[root@linuxidc ~]# docker volume create portainer_data
portainer_data

运行容器：

[root@linuxidc ~]# docker run -d -p 9000:9000 -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer
439cc8a6d44a84f5967534c50d3accc43fbeb578258a52c2683afeb230dd6e04

参数说明：
-d：容器在后台运行；
-p 9000:9000 ：宿主机9000端口映射容器中的9000端口
-v /var/run/docker.sock:/var/run/docker.sock ：把宿主机的Docker守护进程(Docker daemon)默认监听的Unix域套接字挂载到容器中；
-v portainer_data:/data ：把宿主机portainer_data数据卷挂载到容器/data目录；
portainer的安装可以依赖于容器，也可以独立安装

	
使用portainer创建容器<br/>
在命令行下编写Dockerfile文件，打包生成镜像<br/>
使用portainer创建service
选中要创建容器的镜像，如果服务配置正确，会自动启动相应数量的容器

## 3.dockerswarm
更新服务docker service update --force --image registry.co/image service

docker无缝更新docker service update --update-parallelism 1 --update-delay 30s --image registry.pm.bwoilmarine.com/vessel_valuation:1.0.5 vessel_valuation