---
layout: post
title: 单片机中位取反
category: github
description: 单片机中取反~与非的区别！
img: jekyll/jekyll.jpg
keywords: 单片机中位取反~与非的区别！
---

1. 单片机中按位取反~，即0xff 取反则为0。 00000001 取反则为11111110.

2. ！取非。 即true变false， false变true。  那么bit 为1 取非为0.  led = !P1^1 , 把p1的第一个引脚取反。
