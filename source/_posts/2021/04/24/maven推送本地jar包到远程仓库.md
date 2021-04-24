---
title: maven推送本地jar包到远程仓库
abbrlink: e8fffc8d
date: 2021-04-24 13:08:54
categories:
- 工具
- Maven
tags:
- Maven
---
## 安装到本地仓库

```shell
mvn install:install-file -Dfile=non-maven-proj.jar 
            -DgroupId=some.group 
            -DartifactId=non-maven-proj 
            -Dversion=1 
            -Dpackaging=jar
```

<!-- more -->

## 部署到私服

settings.xml 中配置服务器信息

```xml
[...]
  <server>
    <id>internal.repo</id>
    <username>maven</username>
    <password>foobar</password>
  </server>
[...]
```

执行如下命令将本地jar包提交到私服

```shell
mvn deploy:deploy-file -Durl=file://C:\m2-repo \
             -DrepositoryId=服务器<id> \
             -Dfile=your-artifact-1.0.jar \
             [-DpomFile=your-pom.xml] \
             [-DgroupId=org.some.group] \
             [-DartifactId=your-artifact] \
             [-Dversion=1.0] \
             [-Dpackaging=jar] \
             [-Dclassifier=test] \
             [-DgeneratePom=true] \
             [-DgeneratePom.description="My Project Description"] \
             [-DrepositoryLayout=legacy]
```


