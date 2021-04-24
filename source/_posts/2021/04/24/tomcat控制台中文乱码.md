---
title: tomcat控制台中文乱码
abbrlink: fcba60c6
date: 2021-04-24 13:58:34
categories:
- 服务器
- Tomcat
tags:
- Tomcat
---

maven在idea中使用系统控制台，windows系统的默认编码不是UTF-8，而tomcat的默认控制台编码为UTF-8，从而导致乱码

## 解决方案

找到`tomcat`的根目录，`conf`-> `logging.properties`

注释`java.util.logging.ConsoleHandler.encoding = UTF-8`或者将`UTF-8`修改为`GBK`

