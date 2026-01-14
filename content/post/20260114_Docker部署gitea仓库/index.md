---
title: 'Docker部署gitea仓库'

date: 2026-01-14T16:16:00+08:00
lastmod: 2026-01-14T16:16:00+08:00

categories:
  - 服务器笔记
  - 命令集
tags:
  - Docker
  - Centos7
  - Gitea
---
## 1、gitea部署

1）创建项目文件夹及其子文件夹

```
mkdir -p ~/gitea
cd ~/gitea
mkdir -p ~/gitea/{config,data}
```

2）在工程目录(~/gitea)下创建docker-compose.yml

```
vi docker-compose.yml
```

```
version: "3.9"
services:
  server:
    build: .
    image: gitea-pandoc:1.24.3-rootless
    container_name: gitea
    restart: always
    environment:
      - USER_UID=1000
      - USER_GID=1000
    volumes:
      - ./data:/var/lib/gitea
      - ./config:/etc/gitea
      - /etc/timezone:/etc/timezone:ro
      - /etc/localtime:/etc/localtime:ro
    ports:
      - "3000:3000"
      - "2222:2222"
```

3）在项目文件夹下启动gitea

旧版本：

```
docker-compose up -d
```

新版本：

```
docker compose up -d
```

## 2、遇到的问题

错误情况

执行`curl http://localhost:3000`

响应

```
Error response from daemon: Container 71cba76236141dc4599f1efc729d68a0b1f7853159d30211d053372ccfbcabe9 is restarting, wait until the container is running"
```

此时docker日志显示

```
mkdir: can't create directory '/var/lib/gitea/git': Permission denied /var/lib/gitea/git is not writable docker setup failed
```

原因为由于配置的gitea是rootless，因此docker用户出现了权限问题

因此解决方案为

1）将`docker-compose.yml`文件中的`image: gitea-pandoc:1.24.3-rootless`末尾的rootless去掉再执行up

2）修改data与config文件夹的属主

```
sudo chown -R 1000:1000 data config
```

此时访问 `http://localhost:3000`即可正常进入gitea的配置页面，按喜好配置即可
