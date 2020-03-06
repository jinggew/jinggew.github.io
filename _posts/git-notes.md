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

具体做法是：

- 如果不在master分支，先确保切换回master分支

  ```
  git checkout master
  ```

- 进入要备份的`source`文件夹
- 