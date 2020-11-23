## docker：
腾讯云 加速https://cloud.tencent.com/document/product/457/9113 教程

windows下载：https://desktop.docker.com/win/stable/Docker%20Desktop%20Installer.exe
### 安装 卸载
      安装：一、yum安装docker（CentOS 7）
Docker CE 即社区免费版，Docker EE 即企业版，强调安全，但需付费使用。
下面是Docker CE的安装使用
 移除旧的版本：
  $ sudo yum remove docker \                  docker-client \                  docker-client-latest \                  docker-common \                  docker-latest \                  docker-latest-logrotate \                  docker-logrotate \                  docker-selinux \                  docker-engine-selinux \                  docker-engine
 
 安装一些必要的系统工具：
  $ sudo yum install -y yum-utils device-mapper-persistent-data lvm2
 
 添加软件源信息：
  $ sudo yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
 
 更新 yum 缓存：
  $ sudo yum makecache fast
 
 安装 Docker-ce：
  $ sudo yum -y install docker-ce
 
 启动 Docker 后台服务
  $ sudo systemctl start docker
 
 测试运行 hello-world
      [root@localhost docker]# docker run hello-world           Hello from Docker!          This message shows that your installation appears to be working correctly.           To generate this message, Docker took the following steps:          1\. The Docker client contacted the Docker daemon.          2\. The Docker daemon pulled the "hello-world" image from the Docker Hub.              (amd64)          3\. The Docker daemon created a new container from that image which runs the              executable that produces the output you are currently reading.          4\. The Docker daemon streamed that output to the Docker client, which sent it              to your terminal.           To try something more ambitious, you can run an Ubuntu container with:          $ docker run -it ubuntu bash           Share images, automate workflows, and more with a free Docker ID:          https://hub.docker.com/           For more examples and ideas, visit:          https://docs.docker.com/get-started/

      
      
 卸载：1 查看已安装的包 yum list installed | grep docker

      2 yum remove 文件1 文件2


### 设置
状态：systemctl status docker

启动：systemctl start docker

关闭： service docker stop

镜像：
获取镜像：
官网-> docker pull 镜像名[:标签]

其他网站-> docker pull 链接地址/镜像名[:标签]

没有[:标签]会默认下载最新的版本

查看镜像:
docker images

使用tag命令给镜像添加标签:

docker tag img : 1  image : 2

删除的时候可以仅删除副本

查看镜像详细信息:
docker inspect 镜像 : 1

删除和清理镜像:
docker rmi 镜像名: 2
docker rmi 镜像id
清理未被使用的镜像 docker image prune

创建镜像：
 基于容器创建：
 
1 启动容器，进行修改操作。

2 docker commit -m ‘msg’ 镜像id 镜像名: 1

     基于本地模板创建;
     
 基于DockerFile创建:

导入导出镜像：

导出 docker save -o target.tar 镜像id（镜像名:标签）

导入 docker load -i ***.tar

容器

新建容器：

docker create -it 镜像名:标签 command

启动容器：

docker start 容器id

新建并启动

Docker run -it 镜像名:标签 command

查看运行的容器

docker ps
停止和运行的容器 docker ps -a

暂停容器

docker pause 容器id

停止容器

docker stop 容器id

进入容器

docker attach 容器id

docker exec -it b06fae9dcf21 /bin/bash

删除容器

Docker rm 容器id

数据管理

数据卷：-v /D/Docker/redis/data:/data (启动时添加这个参数d盘映射到容器里)

端口映射

docker run -p 3306:3306 --name mysql_80 -e MYSQL_ROOT_PASSWORD=密码 -e TZ=Asia/Shanghai -d 镜像名 mysqld --default-authentication-plugin=mysql_native_password

docker run --name nginx-test -p 8080:80 -d nginx

docker run -d --name myredis -p 6379:6379 redis --requirepass "mypassword"

docker pull docker.io/rabbitmq:3.8-management
docker run -d --hostname rabbitmq --name rabbit -p 5672:5672 -p 15672:15672 rabbitmq
