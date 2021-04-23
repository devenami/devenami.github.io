---
title: git清空提交记录
abbrlink: a4303a1c
date: 2021-04-23 20:12:40
categories:
- 工具
- Git
tags:
- Git
---
## 切换到新的分支

```undefined
   git checkout --orphan latest_branch
```

## 缓存所有文件（除了.gitignore中声名排除的）

```csharp
   git add -A
```

<!-- more -->

## 提交跟踪过的文件（Commit the changes）

```bash
   git commit -am "commit message"
```

## 删除master分支（Delete the branch）

```undefined
   git branch -D master
```

## 重命名当前分支为master（Rename the current branch to master）

```undefined
   git branch -m master
```

## 提交到远程master分支 （Finally, force update your repository）

```undefined
   git push -f origin master
```

来源: [git仓库删除所有提交历史记录，成为一个干净的新仓库](https://www.jianshu.com/p/0b986acd0064)