---
layout: post
title: windows上一键安装Jekyll
category: github
description: windows上快速安装Jekyll
img: jekyll/jekyll.jpg
keywords: jekyll,github,静态web
---

###由于Jekyll的安装依赖ruby环境，而安装ruby，再装devkit，RubyGems后gem install jekyll还会出现各种错误。这些错误可能是应为各个工具的版本不兼容引起的。既然这么麻烦，有没有一个工具一下把所有的都装好呢，当然有撒。直接安装[railsinstaller](http://www.railsinstaller.org/en "railsinstaller")可以保证个工具都兼容， 此工具包含Ruby, Rails, Bundler, Git, Sqlite, TinyTDS, SQL Server Support, Devkit.


 - 下载railsinstaller: http://www.railsinstaller.org/en
 - 安装后环境变量都不用配了, 直接打开CMD，安装Jekyll即可。
```
gem install jekyll
```

 - 装好后就可以查看jekyll的版本了。
```sh
jekyll -v
```
