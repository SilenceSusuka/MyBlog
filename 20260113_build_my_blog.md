# 依靠github pages以及hugo搭建自己的博客网站

## 1、连接本地与github

### 1.1、配置ssh_key

1)使用命令创建ssh公私钥对(使用github注册邮箱)

```
ssh-keygen -t rsa -C "register@mail.com"
```

2）从id_rsa.pub中复制公钥

```
ssh-rsa AAAAB3Nz......Js= register@mail.com
```

3）在github的settings中添加该ssh公钥

4）使用命令测试连通

```
ssh -T git@github.com
Hi SilenceSusuka! You've successfully authenticated, but GitHub does not provide shell access.
```

### 1.2、配置本地git仓库

1)打开文件夹后，clone远程仓库

```
git clone https://github.com/SilenceSusuka/MyBlog.git
```

2)检查remote是否正确以及分支是否正确

```
git remote -v
git branch -vv
```

若remote与branch不正确则分别执行以下设置

```
git remote add origin https://github.com/SilenceSusuka/MyBlog.git
git branch -M main
```

### 1.3、下载博客模板

这边使用hugo进行博客网站搭建，因此可以使用hugo的模板

[https://themes.gohugo.io/](https://themes.gohugo.io/)

下载至本地仓库后提交
