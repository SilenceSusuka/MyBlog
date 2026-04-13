---
title: 'Cursor部署Burp_MCP辅助渗透'
cover: https://blog.silencesusuka.com/images/cover/cover4.jpg
date: 2026-04-13T10:59:00+08:00
lastmod: 2026-04-13T11:00:00+08:00

categories:
  - 工具集
tags:
  - Cursor
  - Burpsuite
  - Mcp
  - LLM
---
## 1）下载MCP-server插件

使用的[Datch大佬的Burpsuite](https://www.52pojie.cn/thread-2005151-1-1.html "https://www.52pojie.cn/thread-2005151-1-1.html")

进入Burp的`扩展`>`BApp商店`，搜索MCP并选择`MCP Server`

![1776066429463](image/index/1776066429463.png)

该扩展默认监听9876端口

## 2）下载监听jar包

在该扩展页面点击`Extract server proxy jar`，下载代理的jar包

![1776066541156](image/index/1776066541156.png)

## 3）Cursor配置

在MCP配置页面添加
![1776066831584](image/index/1776066831584.png)

```json
{
  "mcpServers": {
    "burp":{
      "command":"java",
      "args": [
        "-jar",
        "D:\\burp\\plugin\\MCP\\mcp-proxy.jar",
        "--sse-url",
        "http://127.0.0.1:9876"
      ]
    }
  }
}
```

配置成功

![1776067363551](image/index/1776067363551.png)

## 4）MCP调用结果

成功调用burp进行流量分析

![1776067734177](image/index/1776067734177.png)
