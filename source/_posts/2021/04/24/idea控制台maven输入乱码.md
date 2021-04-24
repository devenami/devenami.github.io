---
title: idea控制台maven输入乱码
abbrlink: ee591c02
date: 2021-04-24 13:04:19
categories:
- 工具
- IDEA
tags:
- IDEA
---

windows平台中文使用的是GB2312编码，而maven使用的不是该编码，导致乱码

<!-- more -->

## 解决方案

打开`settings` -> `Build,Execution,Deployment`-> `Maven` -> `Runner`

修改`VM Options`为`-Dfile.encoding=GB2312`


