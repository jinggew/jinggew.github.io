---
title: git notes
date: 2020-03-07 01:13:12
tags:
- 工具
- hexo
categories: others
description: git tips
typora-root-url: git-notes
---

<!-- more --> 

今天参考 https://www.jianshu.com/p/55f11d8973f0 在github上github pages的仓库下建立了一个source分支，用来存放hexo博客的md源文件，用于备份和以后迁移设备备用。

# 首次备份到新的branch做法

- 如果不在master分支，先确保切换回master分支

  ```
  git checkout master
  ```

- 进入要备份的`source`文件夹

- 初始化git仓库

  ```
  git init
  ```

-  与远程仓库建立连接 

  ```
  git remote add origin git@github.com:yourname/yourname.github.io.git
  ```

-  在本地把源代码提交到本地版本库中 

  ```
  git add .
  git commit -m 'add hexo-blog origin files'
  ```

-  推送到远程仓库的名为source的新分支上面

  ```
  git push origin master:source
  ```

  

# 之后每次备份新的blog文件做法

## 先备份md文件夹

- 进入本地带备份的`source`文件夹

-  在本地把源代码提交到本地版本库中 

  ```
  git add .
  git commit -m 'add new hexo-blog file'
  ```

- 推送到远程仓库的名为source分支

  ```
  git push origin master:source
  ```

## 再部署静态文件

```
hexo g
hexo d 
```

