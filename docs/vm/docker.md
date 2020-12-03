# 常用命令

## 查找、下载、查看images:

可以使用 docker [image] pull 命令直接从 Docker Hub 镜像源来下载镜像。 该命
令的格式为 docker [image] pull NAME [ :TAG] 。

docker pull ubuntu:18.04

使用docker images或docker image ls 命令可以列出本地主机上已有镜像的基
本信息。

使用docker [image] inspect 命令可以获取该镜像的详细信息，包括制作者 、 适应
架构、各层的数字摘要等

使用 docker search 命令可以搜索
Docker Hub 官方仓库中的镜像。 语法为 docker search [op巨on] keyword。


## 容器

创建容器:

```
docker create -it ubuntu:latest
```
-it 表示打开一个交互接口（可以输入命令操作）

docker run 新建并启动容器

```
docker run -t -i ubuntu:14.04 /bin/bash
```
加-d 守护态运行.
--name 指定容器名

docker ps 查看当前运行的容器， 加-a,列出所有容器

可以使用 docker stop 来终止一个运行中的容器

docker start 启动一个容器

docker attach 进入容器进行操作

可以使用 docker rm 来删除一个处于终止状态的容器。


## 网络

容器中可以运行一些网络应用， 要让外部也可以访问这些应用， 可以通过 -P 或 -p 参数来指定端口映
射。

当使用 -P 标记时， Docker 会随机映射一个 49000~49900 的端口到内部容器开放的网络端口。

可以通过 docker logs 命令来查看应用的信息。

-p（小写的） 则可以指定要映射的端口， 并且， 在一个指定端口上只可以绑定一个容器。 支持的格式有
ip:hostPort:containerPort | ip::containerPort | hostPort:containerPort 。


使用 hostPort:containerPort 格式本地的 5000 端口映射到容器的 5000 端口， 可以执行
$ sudo docker run -d -p 5000:5000 training/webapp python app.py
此时默认会绑定本地所有接口上的所有地址。

使用 docker port 来查看当前映射的端口配置， 也可以查看到绑定的地址

```
sudo docker run -d -p 5000:5000 -p 3000:80 training/webapp python app.py
```

## 磁盘

使用 -v 标记来创建一个数据卷并挂载到容器里

下面创建一个名为 web 的容器， 并加载一个数据卷到容器的 /webapp 目录。
$ sudo docker run -d -P --name web -v /webapp training/webapp python app.py

使用 -v 标记也可以指定挂载一个本地主机的目录到容器中去。
$ sudo docker run -d -P --name web -v /src/webapp:/opt/webapp training/webapp python app.py
上面的命令加载主机的 /src/webapp 目录到容器的 /opt/webapp 目录

## Dockerfile

编写完成 Dockerfile 之后， 可以通过 docker build 命令来创建镜像。可以通过 -t 选项指定标签。

基本的格式为 docker build [选项] 路径 ， 该命令将读取指定路径下（包括子目录） 的 Dockerfile， 并将
该路径下所有内容发送给 Docker 服务端， 由服务端来创建镜像。 因此一般建议放置 Dockerfile 的目录为空
目录。 

docker build -t myrepo/myapp /tmp/test1/


