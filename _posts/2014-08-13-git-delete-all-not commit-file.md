---
layout: post
title: git 删除所有没有commit的文件
category: github
description: git删除没有提交的文件，让项目回到干净的环境
img: jekyll/jekyll.jpg
keywords: git删除没有提交的文件
---

1. 让所有tracked 的文件回到untracked
    git reset --hard  
2. 删除所有新增的文件
    git clean -xdf
