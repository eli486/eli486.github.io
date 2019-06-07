---
title: Link Start
author: GJJ
avatar: https://cdn.jsdelivr.net/gh/eli486/cdn@0.3/avatar/1.jpg
authorLink: www.hojun.cn
authorAbout: someone
authorDesc: common
categories: 学习
date: 2019-5-1 08:00:01
comments: true
tags: 
 - web
 - 行千里
keywords: Blog
description: hexo+github自学搭建
photos: https://cdn.jsdelivr.net/gh/eli486/cdn/article/cover/1.jpg
---
<p>
	啪啪啪！终于捣鼓出了一个模板，以后可以在此基础上慢慢⛏。
	看了老多文字教学，始终没弄出想要的样子，照着做还老出错。还是视频教学更适合我，感谢那么多大佬耐心地在B站上传了视频，首先就要记住hojun大佬。
	作为第一篇Blog,先水一下hexo+GitHub Page搭建此博客。
</p>

## Blog の Set
<p>
	准备好Git、Node.js以及github账号
	简单介绍:
	Git:分布式版本控制系统
	Node.js:运行在服务端的javascript(非阻塞与事件驱动)
	(暂不理解两者运行机制，再学习学习。。。)
</p>

<!--more-->
### Bind Git with Your Github account

``` bash
$ git config --global user.name "你的GitHub用户名"
$ git config --global user.email "你的GitHub注册邮箱"
```

### Generadte a SSH key

为什么要配置这个呢？因为你提交代码肯定要拥有你的github权限才可以，但是直接使用用户名和密码太不安全了，所以我们使用ssh key来解决本地和服务器的连接问题。
``` bash
$ cd ~/. ssh #检查本机已存在的ssh密钥
```
如果提示：No such file or directory 说明你是第一次使用git。

生成密匙(id_rsa(私钥)、id_rsa.pub(公钥))：
两种方式：
第一种： 按三次回车
``` bash
$ ssh-keygen -t rsa -C "邮件地址"
```
这是在C盘用户目录下的.ssh下创建了一个默认的名为id_rsa的文件里面存放密钥

第二种：第一次回车后需要命名
``` bash
$ ssh-keygen -t rsa -f  ~/.ssh/随便名字_id_rsa -C "yourmail@xxx.com"
```
这是创建了自定义命名的rsa密钥(涉及多个github更新多个hexo博客：https://www.jianshu.com/p/0ee8b976ceab    https://www.jianshu.com/p/95e00370fa2c?utm_campaign=maleskine&utm_content=note&utm_medium=seo_notes&utm_source=recommendation
留此备学)
补充：
添加Git SSH 提示：Could not open a connection to your authentication agent。
原因：未启动ssh agent
输入：

``` bash
$ eval `ssh-agent -s` (是～键上的那个`）
```


### Add the SSH key and Test it

``` bash
$ ls -a #直接查看所有文件
$ cat .ssh\id_rsa.pub #直接终端打开文件即可
```

复制里面的内容，打开你的github主页，进入个人设置(点用户头像里的那个setting) -> SSH and GPG keys -> New SSH key：
将刚刚复制的id_rsa.pub内容粘贴进去，最后点击Add SSH key。

在 Git Bash 中检测 GitHub 公钥设置是否成功，输入 :

``` bash
$ ssh git@github.com
```
看到：You've successfully authenticated, but GitHub does not provide shell access.就成了。

通过非对称加密的公钥与私钥来完成加密，公钥放置在GitHub上，私钥放置在自己的电脑里。GitHub要求每次推送代码都是合法用户，所以每次推送都需要输入账号密码验证推送用户是否是合法用户，为了省去每次输入密码的步骤，采用了ssh，当你推送的时候，git就会匹配你的私钥跟GitHub上面的公钥是否是配对的，若是匹配就认为你是合法用户，则允许推送。这样可以保证每次的推送都是正确合法的。
(参考学习链接：https://www.jianshu.com/p/860d3e0fff58)





### Install Hexo
<p>
	安装Hexo:
	在Git Bash命令窗口输入:
</p>

``` bash
$ npm install -g hexo-cli
```	


### Create a Blog
<p>
	在想要安装的目录下新建一个你的Blog文件夹

	直接在Git Bash命令窗口输入也行
	初始化：
</p>

``` bash
$ hexo  init "博客文件夹名"
$ npm install #安装依赖包
```


### Create a new post

``` bash
$ hexo new "博客文章名"
```

	在source/_posts中将生成 文章名.md文件


### Run server

``` bash
$ hexo server
```

### Generate static files

``` bash
$ hexo generate
```

### Deploy to remote sites

``` bash
$ hexo deploy
```

### Show the page

输入：
``` bash
$ hexo s -p 4000
```
在浏览器输入loclahost:4000即可看到初始化页面