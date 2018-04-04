---
title: 使用Hexo+GitHub快速搭建个人博客
date: 2017-08-23 15:55:28
tags: Hexo
---
Hexo 是一个基于 Node.js 的静态博客框架，使用非常方便，结合 GitHub 即使是我这样完全不懂后端的小白也能轻松搭建出属于自己的博客。

<!-- more -->

一直想搭建一个自己的博客，之前尝试过用 wordpress 在服务器上搭一个，但是因为自己不熟悉服务端，碰到的坑太多，只好作罢。今天看了 hexo 的文档和学长博客里的文章很快就将博客搭建起来，第一篇博客就记录一下我搭建博客的过程吧。想用Hexo搭建博客的同学建议看下[Hexo官方文档](https://hexo.io/zh-cn/docs/)，文档很详细。

本文针对平台：windows

主要有以下几个大的步骤：
## 安装 [Git](https://git-scm.com/)

版本控制，windows版自带Git bash

## 安装 [Node.js](https://nodejs.org/en/)

服务端JS环境

上面两个软件安装非常简单，基本就是一直下一步就可以了，安装完成之后右键打开 Git bash ，输入 node -v 和 git --version 后，看到版本号就代表安装成功了

{% asset_img git和node.png %}

## 安装 [Hexo](https://hexo.io/zh-cn/)
在bash中输入**npm install hexo-cli -g**回车之后就可以安装Hexo了，安装成功之后使用 **hexo -v** 可以查看 Hexo 的版本号

{% asset_img 安装hexo.png %}

## 配置hexo文件
新建一个文件夹，如 hexo，在这个文件夹中打开 Git bash，执行 **hexo init** 和**npm install**，Hexo将会自动在这个文件夹中生成相应的文件。

文件目录

    ├── _config.yml
    ├── package.json
    ├── scaffolds
    ├── source
    |   ├── _drafts
    |   └── _posts
    └── themes
_config.yml 是博客的配置文件，_posts文件夹里存放markdown格式的文章，theme文件夹里是主题文件
## 安装 hexo server
执行命令 **npm install hexo-server --save**，安装 hexo server 之后就可以在本地预览博客啦，执行命令 **hexo s** 启动本地服务器之后，访问 http://localhost:4000/ 即可。
## 将本地博客部署到Github上
- 首先要注册一个Github账号，然后新建一个名为 **yourUserName.github.io** 的仓库，找到 **Settings** > **Github pages**，随意选择一个主题，保存，默认为 Master 分支。

{% asset_img githubpages.png %}

- 之后建立本机 Git 和 Github 的联系，输入命令 **ssh-keygen -t rsa -C "your_email@example.com"** 创建一对 SSH 秘钥，**clip < ~/.ssh/id_rsa.pub** 复制公钥到剪贴板，粘贴到 Github 用户设置的 **SSH and GPG keys** 中
- git config --global user.name "userName" //设置本机Git的用户名
- git config --global user.email "userName@gmail.com" //填写自己的邮箱
## 将本地文件同步到Github
打开本地 hexo 文件夹下的 _config.yml 文件，在 deploy: 下填写如图所示信息

{% asset_img deploy.png %}

保存后，用 hexo g -d 可以将本地博客同步到 Github 上了。

## 主题
Hexo 有很多其他人已经开发好的[主题](https://hexo.io/themes/)可以选择，只要下载相应的主题文件，并在_config.yml 中修改 theme：就可以了。

## 参考链接
[Hexo官方文档](https://hexo.io/zh-cn/docs/index.html)

[hexo初探---让写作飞起来](http://djl.pub/2017/01/13/hexo初探---让写作飞起来/)