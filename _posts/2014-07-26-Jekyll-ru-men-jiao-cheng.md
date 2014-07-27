---
layout: post
title: Jekyll入门教程
category: github
description: Jekyll入门教程，jekyll demo,本地生成静态站点
img: jekyll/jekyll.jpg
keywords: jekyll,github,静态web
---

###上一章讲了在windows上的jekyll安装，安装好后如何用呢， 如何搭建一个本地的静态web环境呢？


装好jekyll后，如果后续要使用Markdown 标记语言写文章，则需要另行安装rdiscount或者用Textile 标记语言则需要RedCloth,也可以同时安装后续在配置文件里面配所需的标记语言。

```
gem install rdiscount
gem install RedCloth
```

开始写一个简单的demo，文件结构如下
|--_layouts
|-----|--default.html
|--_posts
|-----|--2014-07-26-hello-world.html
|--_config.yml
|--index.html

当然你可以加css，jquery.js进去，我们先只做一个简单的让其运行起来，
###default.html:

```
<!DOCTYPE html>
<html>
<head>
<meta http-equiv="content-type" content="text/html; charset=utf-8" />
<title>{{ page.title }}</title>
</head>
<body>
{{ content }}
</body>
</html>
```
###2014-07-26-hello-world.html


---
layout: default
title: 你好
---

<h2>{{ page.title }} </h2>
<p> 我的第一个主页</p>
<p>{{ page.date | data_to_string }}</p>
```
###_config.yml
```
baseurl: /first
```
###index.html
```
\---
layout: default
title: my blog
\---
<h2>{{ page.title }}</h2>
<p>new file</p>
<ul>
    {% for post in site.posts %}
	    <li>{{ post.date | date_to_string }} 
		<a href="{{ site.baseurl }}{{ post.url }}">
		{{ post.title }}</a></li>
	{% endfor %}


</ul>

```

在项目路径下运行cmd， 输入jekyll server 启动服务器， build成功的话会在项目文件夹下生成一个_site的文件夹，这里面就是生成的静态站点，在浏览器里面输入localhost:4000/first/即可访问站点。 因为config里面的baseurl配的是/first。如果是/, 则可以localhost:4000 直接访问。

如果你的post文章2014-07-26-hello-world.html命名为2014-07-26-你好.html这样带有中文的字符，启动server会出错的：
```
jekyll 2.1.1 | Error:  incompatible character encodings: UTF-8 and GBK
```
所以文件名最后不要用中文，如果非要用，有高手说如下可以解决，但本人没有试过一下方法：


请先设置环境变量执行 set LC_ALL=en_US.UTF-8，set LANG=en_US.UTF-8，2.0及以后版本此方法不行，需修将ruby安装 目录下lib\ruby\gems\2.0.0\gems\jekyll-1.2.0\lib\jekyll下convertible.rb文件中 self.content = File.read(File.join(base, name))改为 self.content = File.read(File.join(base, name), :encoding => "utf-8")，lib\ruby\gems\2.0.0\gems\jekyll-1.2.0\lib\jekyll\tags下include.rb文件中 source = File.read(File.join(includes_dir, @file))改为 source = File.read(File.join(includes_dir, @file), :encoding => "utf-8")，然后再执行jekyll --server
