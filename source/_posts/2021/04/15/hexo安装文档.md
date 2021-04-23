---
title: hexo安装文档
categories:
  - 工具
  - Hexo
tags:
  - Hexo
abbrlink: 8ab3b61c
date: 2021-04-15 23:15:36
---
Hexo是一个快捷、简单并且功能丰富的框架。您仅需要掌握[MarkDown语法](https://daringfireball.net/projects/markdown/)，并使用该语法编写文档，Hexo会立即生成一组带有非常漂亮主题的静态HTML文件。

<!-- more -->

## 安装

### 前提条件

安装Hexo非常容易，仅需要以下两项依赖：

1. [Node.js](https://nodejs.org/en/)
2. [Git](http://git-scm.com/)

如果您的设备已经安装了这些软件，那么恭喜你，你可以跳过安装步骤！

如果没有，您可以跟随下面的章节安装所有的软件。

### 安装Git

* Windows: 下载并安装git
* Mac: 使用Homebrew安装`brew install git`
* Linux(Ubuntu, Debian): `sudo apt-get install git-core`
* Linux(Fedora, Red Hat, CentOS): `sudo yum install git-core`

> 对Mac用户的提醒
> 
> Mac用户必须先从`App Store`安装`XCode`，并在安装完成后选择`Preferences -> Download -> Command Line Tools -> Install`安装命令行工具。否则在Hexo编译静态文件时，可能出现无法意料的问题。

### 安装Node.js

[node.js官方](https://nodejs.org/en/download/)提供了大多数平台的安装包，您可以直接从官网进行下载。

### 安装Hexo

以上软件安装完成后，使用`npm`进行安装

``` bash
$ npm install -g hexo-cli
```

## 初始化项目

使用`hexo init <project>`命令可以初始化一个hexo项目

``` bash
$ hexo init my-site
```

## 测试

使用`hexo s`启动服务进行本地调试

``` bash
$ cd my-site

$ hexo s
```
浏览器访问[http://localhost:4000](http://localhost:4000)即可查看到hexo首页。