---
title: '服务器Docker安装与配置镜像源'

date: 2026-01-14T16:00:00+08:00
lastmod: 2026-01-14T16:00:00+08:00

categories:
  - 服务器笔记
  - 命令集
tags:
  - Docker
  - Centos7
---
Centos7的yum安装可参考：[Centos7配置 yum源](https://blog.silencesusuka.com/post/20260114_centos7%E9%85%8D%E7%BD%AEyum%E6%BA%90/)

## 1、安装docker

1）卸载docker旧版本

```
sudo yum remove docker docker-client docker-client-latest docker-common docker-latest docker-latest-logrotate docker-logrotate docker-engine
```

2）安装相关依赖

```
sudo yum install -y yum-utils device-mapper-persistent-data lvm2
```

3）设置docker稳定版存储库

```
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
```

4）安装docker引擎

```
sudo yum install docker-ce docker-ce-cli containerd.io
```

5）启动docker

```
sudo systemctl start docker
```

6）验证docker是否安装成功

```
sudo docker run hello-world
```

7）设置docker开机自启

```
sudo systemctl enable docker
```

## 2、镜像源配置

1）创建镜像源目录

```
sudo mkdir -p /etc/docker
```

2）写入daemon.json

```
sudo vi /etc/docker/daemon.json
```

```
{
    "registry-mirrors": [
        "https://docker.m.daocloud.io",
        "https://docker.imgdb.de",
        "https://docker-0.unsee.tech",
        "https://docker.hlmirror.com",
        "https://docker.1ms.run",
        "https://func.ink",
        "https://lispy.org",
        "https://docker.xiaogenban1993.com"
    ]
}
```

3）重启docker

```
sudo systemctl daemon-reload
sudo systemctl restart docker
```
