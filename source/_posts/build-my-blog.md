---
title: 搭建自己的博客
date: 2019年12月1日
tags: [hexo, github, travis-ci, blog]
---
# 为什么要搭建自己的博客
在查阅资料的时候，接触到了一个牛人的博客：[菊长的菊花田](http://aicdg.com)，让人眼前一亮。遂心生“歹意”，势要搭建一个自己的博客。

**牛人都有自己的博客，那我也要整一个。**

经调查，前面提到的牛人使用的方案是：**[Jekyll](http://jekyllcn.com/docs/home/)+GitHub**，除此之外还了解到另外一个方案：**[Hexo](https://hexo.io/zh-cn/docs/)+GitHub+[Travis-ci](https://docs.travis-ci.com)**。二者我都尝试搭建了一下，最后选择了后者，仅仅是因为折腾Hexo花费的时间比较多，导致对其更加了解一些。

点击[这里](https://adamcchen.github.io/blog/)查看我使用Hexo+GitHub+Travis-ci方案搭建的博客。

# Jekyll+Github
那个牛人使用的Jekyll模板叫[Space](https://github.com/victorvoid/space-jekyll-template)，我把这个模板
Fork到自己的[Github](https://github.com/adamcchen/lvluo)仓库，然后修改[_config.yml](https://github.com/adamcchen/lvluo/blob/master/_config.yml)，最后在这个仓库的[GitHub Pages配置](https://github.com/adamcchen/lvluo/settings)就可以看到你的博客链接。

**注：**我需要修改_config.yml的原因是我把这个仓库的名字改掉了。

## 修改仓库名字
很多地方建议将博客的仓库名字改为`[你的GitHub用户名].github.io`，这样做的好处是博客链接地址变得更简明，为：https://adamcchen.github.io (adamcchen是我的用户名)。

如果仓库名不采用上述形式，如改为：lvluo，那么博客链接地址会变为：https://adamcchen.github.io/lvluo ，并且需要修改`_config.yml`的`baseurl`和`url`配置。

## gh-pages分支
比较细心的童鞋在仓库的GitHub Pages配置项会发现GitHub Pages服务的源分支为gh-pages，当你打开gh-pages分支，原来Jekyll生成的静态网页都在这个分支。所以GitHub Pages服务的处理流程应该是这样的：
1. 我们在仓库的master分支提交了新的Markdown文件，也就是新的博客文章
1. GitHub Pages服务检测到有新的提交，则触发命令：`jekyll build`，生成静态网页
1. 将静态网页提交到gh-pages分支

当你打开博客链接，访问的就是gh-pages分支的文件。

# Hexo+Github+Travis-ci
使用Hexo生成一个博客工程并上传到GitHub后，我很自然地也按照相同的[套路](https://hexo.io/zh-cn/docs/github-pages)操作。但是却遇到一个奇怪的问题：GitHub Pages配置项默认选择的是master分支，而不能选择gh-pages分支，这样就导致访问博客链接总是显示404。

在解决这个问题之前，我们猜测一下这个方案的“套路”是怎样的：
1. 我们在仓库的master分支提交了新的Markdown文件，也就是新的博客文章
1. Travis-ci检测到有新的提交，则触发命令：`hexo generate`，生成静态网页
1. 将静态网页提交到gh-pages分支

可以看到，这个方案需要使用Travis-ci来完成生成静态网页和更新gh-pages分支的工作，而使用Jekyll的时候是GitHub Pages服务自动完成的。也就是说，GitHub Pages默认支持的是Jekyll。

所以，当我们把仓库名字改为`[你的GitHub用户名].github.io`时，GitHub Pages服务认为这使用的是Jekyll，然而实际上是Hexo，于是出现了问题。

**解决办法是：修改仓库名字。**

修改了仓库名字之后，GitHub Pages配置项就又可以看到我们熟悉的gh-pages分支了。
