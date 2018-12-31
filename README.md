<p align="center">
    <a href="https://www.docker.com/" target="_blank">
        <img src="https://www.docker.com/sites/default/files/mono_vertical_large.png" height="100px">
    </a>
    <h1 align="center">Yii2 PHP Docker Image</h1>
    <br>
</p>

**Stable**
[![Build Status](https://travis-ci.org/yiisoft/yii2-docker.svg?branch=master)](https://travis-ci.org/yiisoft/yii2-docker)
**Development**
[![pipeline status](https://gitlab.com/yiisoft/yii2-docker/badges/master/pipeline.svg)](https://gitlab.com/yiisoft/yii2-docker/commits/master)


This is the repo of the official [Yii 2.0 Framework](http://www.yiiframework.com/) image on [DockerHub](https://hub.docker.com/r/yiisoftware/yii2-php/) for PHP.

**以上皆为官方内容**

## About

修改自官方的 yii2-docker，替换掉官方镜像(debian)中的软件源，使用阿里云的 debian 源，更改的官方 Dockerfile 内的 composer 安装方式，并全局配置 composer 国内源
其他情况看官方 yii2-docker 介绍

## 使用方法
```
    cp .env-dist .env
    
    docker-compose build
    
    上面步骤完成后可以愉快的使用 docker，
    
    使用 composer 方法
    docker-compose run --rm php composer
    比如创建 yii2 项目
    docker-compose run --rm php composer create-project yiisoft/yii2-app-basic /app
    docker-compose up
    运行 http://127.0.0.1:8000 即可查看效果
    遇到 gii 403 的问题，得到容器的 ip 地址以后在 gii 配置即可
```
## 截图
![运行情况](/images/docker.png)

## 以下删除官方介绍，官方详细介绍看官方的连接

(https://github.com/yiisoft/yii2-docker.git)

# windows 中安装方法 
## win10：

假设我们已经安装好了 Docker 运行环境
主要说下 win10 下运行镜像的注意点

1. 修改 .env 
```
	修改下面的内容主要的原因是`win`和`linux`的路径不一样，不修改一下内容，会在`win10`下出现找不着目录的错误
	在文件最上面可以看到这两行注释

	## Windows settings
	# COMPOSE_PATH_SEPARATOR=:

	将其修改为下面的内容

	## Windows settings
	COMPOSE_PATH_SEPARATOR=:

2. `docker-compose up -d`运行容器时出现 `standard_init_linux.go:195: exec user process caused "no such file or directory" `这样的错误，这样的错误的原因是在`win10`下用 notepad++ 编辑文件会在文件末尾加上 win 换行符，利用 git-bash 运行命令 `cat -v xxx.sh` xxx.sh 代表查看的文件，会发现末尾出现了 `^M` 这样的字符，那么我们可以在 git-bash 下运行 `dos2unix xxx.sh` 将其转换成 unix 格式的，然后重新运行 `docker-compose up -d` 会发现一切正常

