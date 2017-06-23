---
title: GIT-SSH配置和使用
subtitle: 
description: GIT-SSH配置和使用
author: huier
email: qiuyuhuier@163.com
language: zh-CN
date: 2016-5-19 14:56:58
tags:
- 技术
categories:
- 目录
comments: true
---

## git-ssh配置和使用

### 1、设置Git的user name和email：(如果是第一次的话)

$ `git config --global user.name "humingx"`

$ `git config --global user.email "humingx@yeah.net"`

### 2、生成密钥

$ ssh-keygen -t rsa -C "humingx@yeah.net"

连续3个回车。如果不需要密码的话。(第一个回车是id名，多个密钥时，需改成不同id)

最后得到了两个文件：id_rsa和id_rsa.pub。

### 3、登陆Github, 添加ssh 。

把id_rsa.pub文件里的内容复制到github设置的ssh-key当中。

### 4、测试：
$ `ssh -T git@github.com`

成功时：

``The authenticity of host 'github.com (207.97.227.239)' can't be established.
    RSA key fingerprint is 16:27:ac:a5:76:28:2d:36:63:1b:56:4d:eb:df:a6:48.
    Are you sure you want to continue connecting (yes/no)?``
    
选择 yes:

```Hi humingx! You've successfully authenticated, but GitHub does not provide shell access.```


>当`Permission denied (publickey).`或者`git pull origin master`操作时，报错：
>Permission denied (publickey).
>fatal: Could not read from remote repository.
>意思是：权限被拒绝（公钥）。无法读取远程库。
>此时需要配置ssh-agent:


### 5、添加密钥到ssh-agent

确保 ssh-agent 是可用的。

ssh-agent是一种控制用来保存公钥身份验证所使用的私钥的程序，其实ssh-agent就是一个密钥管理器，运行ssh-agent以后，使用ssh-add将私钥交给ssh-agent保管，其他程序需要身份验证的时候可以将验证申请交给ssh-agent来完成整个认证过程。

$ `eval "$(ssh-agent -s)"`

>Agent pid 59566

添加生成的 SSH key 到 ssh-agent。

$ `ssh-add ~/.ssh/id_rsa` #不同的密钥对应不同id