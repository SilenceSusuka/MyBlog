---
title: 'Centos7配置yum源'
cover: https://blog.silencesusuka.com/images/cover/cover4.jpg
date: 2026-01-14T10:08:00+08:00
lastmod: 2026-01-14T10:08:00+08:00

categories:
- 服务器笔记
- 命令集

tags:
- Centos7
- yum
---
**1）备份原有源**

```
cp /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup
```

**2）下载阿里云镜像**

```
wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo
```

或者

```
curl -o /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo
```

**3）清除并生成新的缓存**

```
yum clean all # 清除系统所有的yum缓存
yum makecache # 生成yum缓存
```
