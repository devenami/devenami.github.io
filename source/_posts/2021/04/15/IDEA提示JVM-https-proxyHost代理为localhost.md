---
title: IDEA提示JVM https.proxyHost代理为localhost
categories:
  - 工具
  - IDEA
tags: IDEA
abbrlink: 34cc3d33
date: 2021-04-15 21:32:00
---
## 问题描述
IDEA打开`Preferences | Appearance & Behavior | System Settings | HTTP Proxy`会提示一下语句：

```
You have JVM proterty "https.proxyHost" set to "127.0.0.1".
This may lead to incorrect behaviour. Proxy should be set in Settings | HTTP Proxy
This JVM property is old and its usage is not recommended by Oracle.
(Note: Iy could have been assigned by some code dynamically.)
```

出现该问题的原因一般是我们在本地启用了代理软件，代理软件自动修改了JVM代理。
<!-- more -->

## 解决方式

在IDEA工具栏中找到`Help`选项，选择其下的`Edit Custom VM Options...`, 并在次文件内追加以下内容：

```
-Dhttp.proxyHost
-Dhttp.proxyPort
-Dhttps.proxyHost
-Dhttps.proxyPort
-DsocksProxyHost
-DsocksProxyPort
```
