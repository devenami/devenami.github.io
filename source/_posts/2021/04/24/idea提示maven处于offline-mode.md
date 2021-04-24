---
title: idea提示maven处于offline-mode
abbrlink: 3f2709db
date: 2021-04-24 13:05:34
categories:
- 工具
- IDEA
tags:
- IDEA
---

在**pom**文件中新增了一条依赖项，但是将代码克隆到本地后使用**idea**无法下载该**jar**包。提示*offline mode*等等

根据提示可知，当前maven开启了离线模式：仅使用本地仓库中现有的依赖项。

<!-- more -->

## 解决方案

`File -> Settings -> Build,Execution,Deployment -> Maven`关闭`Work offline`即可解决。


