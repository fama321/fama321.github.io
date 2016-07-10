---
layout: post
title: "Let's Start Jekyll !"
date: 2016-07-10 19:09:34 +0800
category: jekyll
tags: Jekyll Markdown YAML Liquid
---

##第一页博客


引用:

[jekyll.bootcss.com][1]
[1]: <http://jekyll.bootcss.com> "jekyll.bootcss.com"


***

##1.头信息

	任何只要包含 YAML 头信息的文件在 Jekyll 中都能被当做一个特殊的文件来处理。头信息必须在文件的开始部分，并且需要按照 YAML 的格式写在两行三虚线之间
	
	---
	layout: post
	title: Blogging Like a Hacker
	---
	
{{ site.title }}

{{ site.url }}

