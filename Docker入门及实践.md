@[toc]
### 导语

学习一门技术，我们不仅仅要看到它的 API，还要站在更高的角度去看待它的发展，它的整个生命周期。

就像 jQuery，它的产生、发展和逐渐的被其他框架代替。

初学 Docker 一定要了解到目前的软件行业有哪些痛点，哪些难点，而 Docker 能够解决哪些，不能解决哪些，是怎么解决的。

不能为了学而学，学死知识始终是不能灵活应用的。

### Docker 兴起的背景，以及我们为什么需要学习 Docker

作为一名前端开发人员，你是不是特别害怕服务器部署一样项目？假设领导交给你了个任务，需要把一个应用部署到五台服务器上。而这一项目需要依赖东西有：node、nginx、mongodb、redis、pm2。如果要在五台服务器上一个一个安装环境，修改配置文件，那一天也搞不完。此外还有一些其他场景，比如五台服务使用一个 mongodb。

是不是很头疼，其实这还是很简单的应用部署，此外还有微服务、集群、日志、监控、针对复杂项目的部署，更是让他头疼。
随着软件行业的不断发展，应用模块的拆分，行业对于软件部署，运维越来越重视了，怎样以最快的速度，最小的资源消耗将复杂应用完整正确地部署 run 起来是一大难题。

软件行业人才济济，在一些大公司不断的摸索和实践中，逐步探索出了一个正确的道路。

这个解决方案就是 Docker，应时而生，天时地利人和。千呼万唤始出来。

今天我们就解开 Docker 的什么面纱，看看它到底有何魅力能够让无数人位置倾倒。

Docker 最初是 dotCloud 公司的一个内部项目，它是基于公司多年云服务技术的一次革新与 2013 年 3 月以 Apache2.0 授权协议在 GitHub 开源，使用 Go 语言编写，基于 Linux 内核的 cgroup，namespace，以及 AUFS 类的 Union FS 等技术，对进程进行封装隔离，属于操作系统层面的虚拟化技术。由于隔离的进程独立于宿主和其它的隔离的进程，因此也称其为容器。

这里有几个重要的概念，使用 Go 语言编写，基于 Linux 内和开发，对进程的封装隔离，操作系统层面的虚拟化技术。

向别人介绍 Docker，能说出这些关键词、概念，就能让人觉得，这货真懂 Docker，大佬啊，前辈啊。然后收割一波粉……哈哈哈。

使用 Docker 的好处：

* 更高效的利用系统资源
* 更快速的启动时间
* 一致的运行环境
* 持续交付和部署
* 更轻松的迁移

Docker 的产生是因为复杂应用的部署，运维等一整套环境的需要。当部署软件比较复杂，需要快速一键部署 test 环境，uat 环境，而且要求以最小的资源，最短的时间去多台部署，这个时间就要学习 Docker，用到 Docker 了。

有人把 Docker 比喻成集装箱，我感觉非常的合适，将一整套环境，软件，配置，以某种方式，打包成一个文件，然后通过某种方式将这个文件展开，形成一套流程的部署流程。


有的人谁说，前端部署很简单的啊，就是把编译后的静态文件，直接丢到一个 Nginx 映射的目录里就行了。那么不用 Docker。有这样想法的人，是当不了架构师的，也没办法和运维，软件实施沟通软件部署中的问题。

有时候别人问我，学那么多技术干嘛啊，前端这一岗位的技术还学不精，学那些乱七八糟的干嘛？

我沉吟片刻回答他说：我不断的学习，接受新事物，是为了更了解所在的世界。希望能够照亮内心，也能照亮其他人。

### Docker 的三大概念，镜像、容器、仓库介绍

Docker 这个东西只有三个概念，其中一个仓库概念还是很少操作的。所以算是一个很简单的技术。当然我们不去细究底层。

Docker 有三大概念，仓库、镜像、容器。

仓库是存放镜像的地方，这个很像 npm 的包管理器，我们把一个包编写好推送到仓库，需要的时候再从仓库里获取到。很方便的包管理器，在 Docker 里叫做镜像仓库。

Docker 的默认仓库是 DockerHub https://hub.docker.com/。当然国内也有一些仓库管理，也可以自己搭建一个，使用 Harbor。

镜像： Docker 镜像是一个特殊的文件系统，除了提供容器运行时所需的程序、库、资源、配置等文件外，还包含了一些为运行时准备的一些配置参数（如匿名卷、环境变量、用户等），镜像有拉去，推送，运行，删除，改名，

容器的实质是进程，但与直接在宿主执行的进程不同，容器进程运行于属于自己的独立的 命名空间

镜像（Image）和容器（Container）的关系，就像是面向对象程序设计中的 类 和 实例 一样，镜像是静态的定义，容器是镜像运行时的实体。容器可以被创建、启动、停止、删除、暂停等。

### 初入 Docker 的前端需要掌握哪些指令，以及 Docker 指令大全

Docker 的命令其实并不是很多，常用的就是 run，pull，还有一些查看状态和停止运行的。

下面我详细介绍一些最常用的命令，不常用的后续工作中有用到可以查查文档。
```
docker run -d --name="mynginx" -p 8080:80 nginx
```

![在这里插入图片描述](https://images.gitbook.cn/6e53cc90-bdb4-11ea-9efc-ab9a6caf88c6)

浏览器访问 8080 端口就可以看到 nginx 的欢迎页面

![在这里插入图片描述](https://images.gitbook.cn/e476fba0-bdb3-11ea-b96f-cbd921d57de1)

执行这个命令，首先会从本地寻找 nginx 的镜像，如果找不到，就会去从远程库拉取，拉去到本地后，然后运行。

参数解释

- `-d` 后台运行容器，并返回容器 ID
- `--name="mynginx"` 为容器指定一个 mynginx 名称
- `-p` 指定端口映射，格式为：`主机（宿主）端口:容器端口`

运行完成后会返回一个 id，这个就是容器的 id。

运行：
```
docker container ls
```

![在这里插入图片描述](https://images.gitbook.cn/2bc75c70-bdb4-11ea-b96f-cbd921d57de1)

查看所有正在运行的容器，这个图标从左到右分别是

- CONTAINER：ID 容器的 id
- IMAGE：容器所属的镜像
- COMMAND：运行的命令
- CREATED：创建时间
- STATUS：状态 UP 是正在运行
- PORTS：是容器对外的 ip + 端口与容器内部的端口
- NAMES：就是容器的名称，我们在运行时指定的

知道了容器正在运行，我们可以使用 http 协议访问启动的容器服务，在浏览器输入 localhost:8080 即可看到。

启动了一个容器就能对其进行管理，如暂停、停止、删除、重新启动，这些 Docker 都是支持的。

```
docker stop/restart/start mynginx

```
- stop 停止一个容器
- restart 重启容器
- start 启动容器

三个命令都支持同时操作多个容器，可以使用容器 id，也可以使用容器名称，id 只用写前 4 位。


删除容器使用，也可以同时删除多个容器：
```
docker rm mynginx
```

![在这里插入图片描述](https://images.gitbook.cn/63d88a80-bdb4-11ea-ae16-ff3d92a1af13)

容器操作还有一个很有用的指令，虽然大多数用不到，但确实很有用：

```
docker exec -t -i mynginx /bin/sh
```

![在这里插入图片描述](https://images.gitbook.cn/44afb430-bdb4-11ea-aa7b-493850d34acd)

运行此命令可以进入到容器内部，进入之后，可以操作容器内部的文件，查看状态，进程这类的，非常好用，强大。
比如我们要将一个目录加到 nginx 的配置文件里，使其能够外部访问。就可以进入其中操作。
exit 退出命令行

以上就是我们经常用到的容器的操作命令

此外还有
查看容器日志
```
 docker logs -f mynginx
```

查看容器进程信息
```
docker top mynginx
```

列出容器
```
docker ps
```

说完 Docker 的容器操作指令，我们再来说说 Docker 的镜像指令，

列出本地所有的镜像
```
docker images
```

给镜像重命名
```
docker tage nginx local/nginx
```
docker pull nodejs   拉取一个镜像
docker search nodejs  搜索镜像
docker login 登录仓库
docker logout 登出
docker push nginx 将本地镜像推送到镜像仓库 推送都有命名要求的，都会用户名，所以不会镜像重名

只有在推送是才会用到以上这几个命令

此外镜像还有一个重要的命令， build
构建一个镜像

```
docker build -t myimage .
```
这个命令执行时会默认去寻找当前目录的 Dockerfile 文件，根据其中的编写的内容进行构建镜像

这个过程会将当前目录所有文件上传到镜像中，作为上下文，所以说 要构建的时候千万不要把 node_module 文件放到镜像里。

```
docker container prune
```
会将所有已停止的容器清空。

命令行思维导图
![在这里插入图片描述](https://images.gitbook.cn/0c0731b0-bdc0-11ea-8c58-1b755ebce95b)

### 初入 Docker 需要注意哪些问题

首先一定要搞清楚三个概念
仓库是存储镜像的地方
镜像是有个有层级的文件系统
容器是有镜像运行而来的一整套环境，应用。

其次，常用的命令 run start stop 查看镜像，查看容器状态的命令一定要知道，启动，停止。能看懂容器运行的状态。

如果 docker 是在虚拟机里启动的，一定要注意，访问服务不是用一定要用虚拟机的 ip。

很多命令都有很多可选的参数，工作中要熟记几个常用的参数，如 run 的-p -d --name  这几个参数。

### Dockerfile 的入门编写
每一个镜像都是别人编写好，构建好，推送到库给我们下载使用的，这些镜像不是无中生有，自己生产的，Docker 构建镜像使用 Dockerfile 来编写

Dockerfile 的编写非常容易上手，只需要记住两三个指令就可以做成一个部署静态环境的镜像，最常用的有
FROM  定义依赖镜像
COPY  复制文件， 第一个参数是构建上下文的路径，第二个参数是镜像中的路径
WORKDIR  定义工作目录，没有目录会自动创建
RUN 在 docker build 执行命令 如 npm install npm build
CMD 在 docker run 时运行执行命令

此外还有一些相比不常用的命令
ADD 可以自动解压 压缩文件到指定目录
ENTRYPOINT 作用与 CMD 相似，都是在指定容器启动程序及参数
ENV 设置环境变量，定义了环境变量，那么在后续的指令中，就可以使用这个环境变量。
ARG 构建参数，与 ENV 作用一至
VOLUME 定义匿名数据卷。在启动容器时忘记挂载数据卷，会自动挂载到匿名卷。
  作用  避免重要的数据，因容器重启而丢失，这是非常致命的。
       避免容器不断变大。
EXPOSE 声明端口
USER 用于指定执行后续命令的用户和用户组
HEALTHCHECK  用于指定某个程序或者指令来监控 docker 容器服务的运行状态。
ONBUILD 用于延迟构建命令的执行
![在这里插入图片描述](https://images.gitbook.cn/fa351f10-bdbf-11ea-b4ea-b7073bc24068)

### Docker 练手小任务

docker 运行 nginx 以 8090 端口启动，并以 nginx-container 容器名启动

docker 安装 MongoDB 以 27017 端口访问

使用 docker 配置 nginx 一个静态资源目录外部访问

启动一个 express 应用

### 使用 Docker 镜像部署前端单页面应用
使用 Docker 部署前端应用非常简单，单页面应用都是编译好的静态资源，只需要我们将静态资源的目录配置到 nginx 的配置里就可以了

Dockerfile 的内容
```
FROM nginx

WORKDIR /mywebapp

COPY ./dist /usr/share/nginx/html/
```
稍稍解释一下这几句命令，
第一行 使用 nginx 作为基本镜像构建
第二行 将工作目录设置为 mywebapp 没有此目录会自动创建
第三行 将 dist 目录拷贝到/usr/share/nginx/html/

这里的/usr/share/nginx/html/ 是 nginx 的默认 web 服务映射路径，只要存到这里的东西，开启服务后都可以访问的到

执行命令构建
```
docker build -t pmcimage .
```

运行起来看一下效果

```
docker run -d -p 80:80 pmcimage
```
![在这里插入图片描述](https://images.gitbook.cn/1f0dc320-bdb4-11ea-a6f5-e3d8406080eb)
![在这里插入图片描述](https://images.gitbook.cn/57b73990-bdb4-11ea-8c58-1b755ebce95b)

这是最简单的将一个静态资源包做成一个镜像，进行部署并通过浏览器访问

复杂一点的，将项目包的安装，编译，都做到镜像里面

```
FROM node:10-alpine as builder
WORKDIR /code
COPY package.json /code
RUN npm install --registry=https://registry.npm.taobao.org
ADD . /code
RUN npm run build
FROM nginx:10-alpine
COPY ./dist /usr/share/nginx/html/
```
使用 nodejs 作为镜像，复制 package.json 到工作目录 code，安装依赖包，将项目源码放到 code 目录，编译
编译完成后，已 nginx 作为基础镜像，将编译后的./dist 存放到/usr/share/nginx/html/中

![在这里插入图片描述](https://images.gitbook.cn/36ea2920-bdb4-11ea-b619-db0cf7b7dda7)


有些时候我们会问，第一次使用的时候我怎么知道要将部署的静态资源部署 COPY 到/usr/share/nginx/html/目录里?

这个时候我们就要去 Docker hub 的官网去查询 nginx 镜像的相关介绍，文档了。

这个链接就是 nginx 镜像的介绍，写的很清楚，配置，映射静态资源，使用外部端口
![在这里插入图片描述](https://images.gitbook.cn/0b2553a0-bdb4-11ea-b619-db0cf7b7dda7)
每一个应该都有自己的介绍，我们要想用好这些基本镜像，就需要先查阅他们的文档。很多没有带作者的镜像都是官方编写的文档，安全和质量都是有保障的。所以大家可以放心使用。

镜像名后面加上**:alpine** 是表明使用使用的版本，alpine 是一种压缩的，极小体积的镜像，对于网络不太好，内存不够大的工作环境很有帮助。

### 使用 Docker 镜像部署 Node.js 应用
我们使用 express 生成一个应用，并将启动端口改为 8070
在根目录创建一个 Dockerfile
写入
```
FROM node:alpine as builder
WORKDIR /code
COPY package.json /code
RUN npm install --registry=https://registry.npm.taobao.org
ADD . /code
CMD npm start
```

分别运行下面三行指令
```
docker build -t express-images .

docker images

docker run -d -p 8070:8070 express-images
```
![在这里插入图片描述](https://images.gitbook.cn/11193170-bdb7-11ea-b96f-cbd921d57de1)


![在这里插入图片描述](https://images.gitbook.cn/1bbf05f0-bdb7-11ea-a6f5-e3d8406080eb)


![在这里插入图片描述](https://images.gitbook.cn/28a10ed0-bdb7-11ea-b96f-cbd921d57de1)
运行启动后 浏览器访问就会看到以下页面
![在这里插入图片描述](https://images.gitbook.cn/af002020-bdb6-11ea-8603-9d57c1189aea)

### 兴趣探索 Docker 生态一览
**Docker Desktop**

Docker 官方提供了一种 GUI 的方式操作镜像，容器，叫做 Docker Desktop，运行，搜索镜像，只需要点点点，就能操作，非常傻瓜式，简单方便。

**Docker Compose**
		Docker Compose 是 Docker 官方编排（Orchestration）项目之一，负责快速的部署分布式应用。定义和运行多个 Docker 容器的应用，比如说你们的项目是一种微服务的方式开发的，有多个镜像，镜像之间有关联。非常适合需要多个容器相互配合来完成某项任务的情况，例如要实现一个 Web 项目，除了 Web 服务容器本身，往往还需要再加上后端的数据库服务容器，甚至还包括负载均衡容器等。

**Docker Machine**
		Docker Machine 是一种可以让您在虚拟主机上安装 Docker 的工具，并可以使用 docker-machine 命令来管理主机。
Docker Machine 也可以集中管理所有的 docker 主机，比如快速的给 100 台服务器安装上 docker。

**Harbor**
		用于管理，扫描，具备角色管理权限的镜像管理工具。比官方的 Docker Hub 强大。开源，可以自己部署。

**Docker Rest API**
Docker 是可以通过 Http 接口来访问的内部数据的。 需要开启服务。可以参考我写的一篇博客 
https://blog.csdn.net/github_35631540/article/details/107025096


**Kubernetes***
简称 k8s

作用
可移植: 支持公有云，私有云，混合云，多重云（multi-cloud）
可扩展: 模块化， 插件化， 可挂载， 可组合
自动化: 自动部署，自动重启，自动复制，自动伸缩/扩展

特点
可移植: 支持公有云，私有云，混合云，多重云（multi-cloud）
可扩展: 模块化， 插件化， 可挂载， 可组合
自动化: 自动部署，自动重启，自动复制，自动伸缩/扩展

### 结语
容器是一个趋势，不可逆转，就算没有 Docker 也有其他的产品代替。做容器管理，集群，k8s 的公司都比较有钱，而且项目都比较大。这些东西基本上都是开源的，GitHub 上有很多，像 rancher、kubesphere、蓝鲸，还有其他前端听都没听过的一些单词。

作为一名前端，不仅要脚踏实地干好自己的本职工作，还要仰望星空，去探索更广阔的天空。

谢谢，由于我也是刚接触这一块，学了 Docker 一个多月，大家有什么问题，想交流的都可以找我聊，也欢迎大家关注我的博客：

> <https://fizzz.blog.csdn.net/>

谢谢阅读。


----------
本文首发于 GitChat，未经授权不得转载，转载需与 GitChat 联系。
