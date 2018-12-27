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

修改自官方的 yii2-docker，替换掉的官方镜像中的软件源，使用阿里云的 debian 源
更改的官方 Dockerfile 内的 composer 安装方式，并全局配置的 composer 国内源
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
    运行 http://127.0.0.1:8000 即可查看效果
    遇到 gii 403 的问题，得到容器的 ip 地址以后在 gii 配置即可
```

## 以下是官方介绍

### Available versions for `yiisoftware/yii2-php`

```
7.2-apache, 7.1-apache, 7.0-apache, 5.6-apache
7.2-fpm, 7.1-fpm, 7.0-fpm, 5.6-fpm
```

## Setup

    cp .env-dist .env

Adjust the versions in `.env` if you want to build a specific version.

> **Note:** Please make sure to use a matching combination of `DOCKERFILE_FLAVOUR` and `PHP_BASE_IMAGE_VERSION`


## Configuration

- `PHP_ENABLE_XDEBUG` whether to load an enable Xdebug, defaults to `0` (false)
- `PHP_USER_ID` (Debian only) user ID, when running commands as webserver (`www-data`), see also [#15](https://github.com/yiisoft/yii2-docker/issues/15)


## Building

    docker-compose build


## Testing

    docker-compose run --rm php php /tests/requirements.php

### Xdebug

To enable Xdebug, set `PHP_ENABLE_XDEBUG=1` in .env file

Xdebug is configured to call ip `xdebug.remote_host` on `9005` port (not use standard port to avoid conflicts),
so you have to configure your IDE to receive connections from that ip.

If you are using macOS, you can fill `xdebug.remote_host` with `host.docker.internal`, due to a network limitation on mac (https://docs.docker.com/docker-for-mac/networking/#port-mapping)

    ### (macOS) configuration
    xdebug.remote_host=host.docker.internal

## Documentation

More information can be found in the [docs](/docs) folder.


## FAQ

- Error code `139` on Alpine for PHP `5.6-7.1` results from a broken ImageMagick installation         
