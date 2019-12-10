---
title: 修改本地仓库所对应的远程仓库地址
date: 2019-12-03 12:00:00
tags: GIT
---

我克隆了一个Github上的工程到本地，现在需要把本地仓库所指向的远程仓库指向Gitee的一个同样内容的仓库，因为Github太慢，而Gitee是国内的，速度快。操作如下：

```shell
$ cd /the/path/of/your/project
$ git remote rm origin
$ git remote add origin https://gitee.com/adam_cchen/hexo-theme-Chic.git
$ git checkout master
$ git branch --set-upstream master origin/master
$ git pull
```
