---
title: maven编译时统一文件格式
abbrlink: d1cd6a54
date: 2021-04-24 13:21:31
categories:
- 工具
- Maven
tags:
- Maven
---
maven在编译时提示以下信息：编码GBK的不可映射字符

我们直接将项目改为UTF-8编码，再次尝试编译发现问题仍未解决。那我们就需要在`pom.xml`文件中，指定当前项目的文件格式来解决这个问题。

<!-- more -->

## 方案一：

在pom.xml的/project/build/plugins/下的编译插件声明中加入下面的配置：<encoding>UTF-8</encoding>

即：

```xml
<plugin>
    <groupId>org.apache.maven.plugins</groupId>	
    <artifactId>maven-compiler-plugin</artifactId>
    <version>3.1</version>
    <configuration>
        <source>1.7</source>
        <target>1.7</target>
        <encoding>UTF-8</encoding>
    </configuration>
</plugin>
```

## 方案二：

在pom.xml的/project/properties/下的属性配置中加入下面的配置：

<maven.compiler.encoding>UTF-8</maven.compiler.encoding>

即：（有第一句即可）

```xml
<properties>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    <maven.compiler.encoding>UTF-8</maven.compiler.encoding>
</properties>
```

## 引用

[maven错误解决：编码GBK的不可映射字符](https://blog.csdn.net/EvelynHouseba/article/details/16114353)