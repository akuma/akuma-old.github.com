---
layout: post
title: "搭建 Octopress 笔记"
date: 2011-12-01 23:36
comments: true
categories: 
---

关于 Octopress 的搭建步骤，虽然网上资料不少，但还是写出来备忘一下。

### 安装 RVM

选择多用户安装，默认安装到 /usr/local/rvm 目录下：

``` sh
$ sudo bash < <(curl -s https://raw.github.com/wayneeseguin/rvm/master/binscripts/rvm-installer)
$ sudo rvm install 1.9.2 && rvm use 1.9.2
```

### 安装 Octopress

先执行：

``` sh
$ git clone git://github.com/imathis/octopress.git octopress
$ cd octopress
```

在提示是否加载当前目录下的 .rvmrc 文件时输入 y。
继续执行命令：

``` sh
$ sudo gem install bundler
$ sudo bundle install
$ rake install
```

### 发布到 Github Pages

``` sh
$ rake setup_github_pages
```
根据提示输入 Github Pages 的代码库地址。

生成静态页面并发布到 Github Pages:

``` sh
$ rake generate
$ rake deploy
```
最后，将源代码提交到 Github:

``` sh
$ git add .
$ git commit -m 'First Octopress commit.'
$ git push origin source
```
