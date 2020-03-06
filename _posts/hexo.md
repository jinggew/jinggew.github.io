---
title: hexo
date: 2019-12-09 17:03:08
tags:
- 工具
- hexo
categories: others
typora-root-url: hexo
---

# 1 配置

## 1.1 deploy免输入密码

 修改```_config.yml```中deploy的参数，部署仓库以SSH的方式发布不需输入密码，反之如果以HTTPS的方式发布则需要密码。 

```
# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:
  type: git
  repo: git@github.com:yourname/yourname.github.io.git
  branch: master
```

## 1.2 typora加网页正常显示图片

- typora选择

  ![](image-20191210162451322.png)

- 在md文件开头加上```typora-root-url: file-name-of-md```

- 插入图片时使用md命令为：```![](name.png)```

  - 注意如果是截图，需要手动修改为这个格式
  - 去掉自动生成的斜杠/
  - 如果是首次截图会自动生成同名文件夹，之后的图片同时保存到同一个文件夹。

# 2 日常使用

## 2.1 常用命令

- 新建文章

  ```python
  hexo new "title"
  ```

- 添加标签

  ```
  tags:
  - tag1
  - tag2
  ```

- 添加分类

  ```python
  categories: cat1
  ```

- 启动服务器，本地测试

  ```
  hexo s
  ```

- 发布到github

  ```
  hexo clean && hexo g && hexo d
  ```

## 2.2 开头代码模板

```python
title: hexo
date: 2019-12-09 17:03:08
tags:
- 工具
- hexo
categories: others
typora-root-url: hexo
```

## 2.3 修改文章标题

如果需要改文章标题，注意一下几点避免404：

① 修改md文件内开头标题`title: file name`

② 修改md文件内开头`typora-root-url: file-name`

③ 修改md文件名`file-name.md`

④ 修改对应的图片文件夹的名字`file-name`

注意md文件和图片文件夹，在hexo新建全英文名的文件的时候，都会自动生成为有`-`间隔的形式。所以在typora引用图片路径url的时候，也要加上。

## 2.4 图床

考虑后期可能本地图片数量太多占内存，可能需要使用图床。

七牛云图床需要自己另外付费购买域名。

github作图床的话，举例图片链接为https://jinggew.github.io/2020/02/04/American-English/image-20200204160431912.png，但是加载速度会很慢。暂时放弃之。