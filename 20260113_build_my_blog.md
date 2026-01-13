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
