---
title: tomcat修改默认端口号
abbrlink: 2a05b873
date: 2021-04-24 14:01:24
categories:
- 服务器
- Tomcat
tags:
- Tomcat
---

tomcat的端口配置主要在`${tomcat_home}/conf/server.xml`中，如果修改端口号，最好将下面三个位置同时修改。

## 修改server标记

```xml
<Server port="8005" shutdown="SHUTDOWN">
</Server>
```

## 修改web端口

```xml
<Connector port="8080" protocol="HTTP/1.1"
                connectionTimeout="20000"
                redirectPort="8443" />
```

## 修改AJP端口

```xml
<Connector port="8009" protocol="AJP/1.3" redirectPort="8443" />
```


