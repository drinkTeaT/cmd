## docker：

### 安装 卸载
      安装： yum install docker-ce docker-ce-cli containerd.io

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
暂停容器
docker pause 容器id
停止容器
docker stop 容器id
进入容器
docker attach 容器id
删除容器
Docker rm 容器id

数据管理
数据卷：将容器数据映射到主机中
