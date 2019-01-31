# Docker学习笔记

---

### mac安装docker

在https://hub.docker.com 注册账号 并下载客户端

### 本地创建镜像

* 在本地新建目录

mkdir -p /data/docker

* 创建本地Dockerfile并编辑

touch Dockerfile && vim Dockerfile

<code>
  ## 指定这个镜像的基础是什么，我们选择了node: 8.9.3这个版本作为基础镜像
  FROM node:8.9.3

  MAINTAINER stoneship stoneship <258137678@qq.com>

  ##安装node相关依赖
  RUN \
  npm install yarn -g \
  yarn global add nrm && \
  nrm use taobao &&\
  yarn global add vue-cli &&\
  yarn global add cross-env

  ## 安装nginx

  ## 安装数据库...

  ## 创建一个目录
  RUN mkdir /data
  ## 指定命令运行的目录
  WORKDIR /data
</code>

* 创建本地镜像

docker build -t frontdocker .

>> frontdocker为镜像名

* 重命名镜像

docker tag frontdocker chenh666/drontdocker:latest

* 推送镜像

docker push chenh666/frontdocker:latest



### 一些常见命令

* 查看docker版本

docker -version

* 查看docker镜像

docker images

* 查看运行的容器

docker ps -a

* 删除容器

docker rm containerID (容器ID)

* 删除images

docker rmi imageID (镜像ID）



