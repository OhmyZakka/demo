
# Docker

Docker是Docker.Inc公司开源的一个基于LXC技术之上构建的Container容器引擎，源代码托管在GitHub上，基于Go语言并遵从Apache2.0 协议开源。   

Docker是通过内核虚拟化技术（namespaces及cgroups等）来提供容器的资源隔离与安全保障等。由于Docker通过操作系统层的虚拟化实现隔离，所以Docker容器在运行时，不需要类似虚拟机（VM）额外的操作系统开销，提高资源利用率。   

Docker[官方网站](http://www.docker.com/)

### Docker三大核心模块
- 构建(buid)
- 运输()
- 运行(run)  
### Docker组件
- 镜像（Image）
- 容器 (Container)
- 仓库 (Repository)

### Containers vs VMs



### Docker与OpenStack区别

|类别	|Docker	|OpenStack|
|-------|-------|---------|
|部署难度|非常简单|组件多，部署复杂，功能强大|
|启动速度|秒级   |分钟级|
|执行性能|和物理系统几乎一致|VM会占用一些资源|
|镜像体积|镜像是MB级别|虚拟机镜像GB级别|
|管理效率|管理简单|组件相互依赖，管理复杂|
|隔离性 |隔离性高|彻底隔离|
|可管理性|单进程、不建议启动SSH|完整的系统管理|
|网络连接|比较弱|借助Neutron可以灵活组件各类网络架构|


### Docker能干什么
    
- 代码流水线管理
- 开发效率
- 的
- 应用隔离
- 服务器整合
- 调试能力
- 多租户
- 快速部署

### 为什么用Docker
- 技术储备
- 跟上节奏、提升自身技术
- 符合当前业务需求   



### Docker改变了什么###
- 面向产品：产品交付
- 面向开发：简化环境配置
- 面向测试：多版本测试
- 面向运维：环境一致性
- 面向架构：自动化扩容（微服务）

### Docker Demon部署 

配置yum源

	$ cat >/etc/yum.repos/docker.repo<
	[dockerrepo]
	name=Docker Repository
	baseurl=https://yum.dockerproject.org/repo/main/centos/7
	enabled=1
	gpgcheck=1
	gpgkey=https://yum.dockerproject.org/gpg
	EOF

通过yum直接安装   

	$ yum -y install docker
启动Docker

	$ systemctl start docker.service   
开机启动Docker

	$ systemctl enable docker.service


帮助，Docker

	$ docker --help
概要信息

	$ docker info
镜像查看

	$ docker images
容器查看,即进程查看

	$ docker ps -a
###Docker 镜像常用命令###
**搜索镜像**
搜索可用的centos的Docker镜像

	$ docker search centos
**获取镜像**
下载centos镜像(pull images)

	$ docker pull centos:latest
**查看镜像**
列出images

	docker images

列出所有的images（包含历史）

	$ docker images -a

显示镜像的所有层(layer)

	$ docker images --tree
**删除镜像**
删除一个或多个image

	docker rmi  <image ID>
**导入/导出镜像**
导出一个镜像

	$ docker save centos > /tmp/centos.tar.gz
导入一个镜像

	$ docker load < /tmp/centos.tar.gz

### Docker 容器常用命令
创建一个容器

	$ docker run centos /bin/echo "hello world"
运行一个容器

	$ docker run --name mydocker -t -i centos /bin/bash
