---
title: '使用Cloudflare部署v2ray实现代理'
cover: https://blog.silencesusuka.com/images/cover/cover3.jpg
date: 2026-04-10T15:44:00+08:00
lastmod: 2026-04-10T16:00:00+08:00

categories:
  - 服务器笔记
tags:
  - Cloudflare
  - Proxy
  - V2ray
---


使用cmliu大佬的[github项目](https://github.com/cmliu/edgetunnel "https://github.com/cmliu/edgetunnel")，膜拜大佬


先进入[cloudflare控制台](https://dash.cloudflare.com/ "https://dash.cloudflare.com/")，在侧栏选择 `Workers和Pages`，点击`创建应用程序`，并且选择`部署pages`

![1775806529623](image/index/1775806529623.png)

![1775806610992](image/index/1775806610992.png)


导入开头提到的[github项目](https://github.com/cmliu/edgetunnel "https://github.com/cmliu/edgetunnel")，这里直接下载压缩包后上传文件导入

![1775806653202](image/index/1775806653202.png)

![1775806735910](image/index/1775806735910.png)

在成功后选择`继续处理项目`

![1775806785441](image/index/1775806785441.png)


在`设置`>`变量和机密`中，添加密钥，变量名为`ADMIN`，变量值为后续登录使用的密码(**注意使用强密码**)

![1775806828207](image/index/1775806828207.png)


接着在`设置`>`绑定`中绑定KV命名空间，命名为`KV`

![1775807058457](image/index/1775807058457.png)

如果没有KV空间的话，就回到主页面查找 `Workers KV`创建一个空的KV空间，随便填个名称即可

![1775807004166](image/index/1775807004166.png)


最后全部设置完后页面如下，确保含有名称为`ADMIN`的变量以及名称为`KV`的KV命名空间

![1775807099840](image/index/1775807099840.png)


保存后，在刚刚的项目页面选择`创建新的部署`

![1775807276949](image/index/1775807276949.png)


重新上传一次前文[github项目](https://github.com/cmliu/edgetunnel "https://github.com/cmliu/edgetunnel")的压缩包，点击`保存并部署`(上传文件不需要任何更改，此操作只是为了保存刚刚设置的变量)

![1775807324908](image/index/1775807324908.png)

![1775807428455](image/index/1775807428455.png)


直接访问页面url

![1775807505913](image/index/1775807505913.png)

![1775807988757](image/index/1775807988757.png)

出现welcome to nginx就代表部署好了

此时在url中加入 `/admin`路径，即 `https://xxxxxx.pages.dev/admin`，输入刚刚`ADMIN`变量所设的密码即可登录后台，获取订阅链接

![1775807594206](image/index/1775807594206.png)

![1775807748487](image/index/1775807748487.png)

*注：请求使用情况需要额外配置API令牌才可显示*

客户端使用[v2rayN](https://github.com/2dust/v2rayN "https://github.com/2dust/v2rayN")，在订阅设置中填入网站显示的订阅地址并更新订阅即可

![1775808331384](image/index/1775808331384.png)
