---
layout: posts
title: 利用Jekyll在Github Pages上搭建静态博客网站
tags: [Jekyll, Github Pages]
---

今天学习内容是在Github Pages上host自己的blog。从Wordpress转移的原因有二：一是其Markdown对代码的支持不好，一是Wordpress本身太过冗杂，有太多我不需要的功能。

Github Pages上有推荐用[Jekyll](https://jekyllrb.com)来写博客。经过一些简单的查询，发现Jekyll是一个很好的工具。其功能是将纯文本转换成静态博客网站，正符合我的需要。其中文官网对自己的功能描述如下：

>Jekyll 的核心其实是一个文本转换引擎。它的概念其实就是：你用你最喜欢的标记语言来写文章，可以是 Markdown, 也可以是 Textile, 或者就是简单的 HTML, 然后 Jekyll 就会帮你套入一个或一系列的布局中。在整个过程中你可以设置 URL 路径，你的文本在布局中的显示样式等等。这些都可以通过纯文本编辑来实现，最终生成的静态页面就是你的成品了。

明白该工具的用途后便可以进行配置。Github Pages本身支持自动利用Jekyll生成站点，所以并不需要安装过程。但是假如想在本地进行网页开发的话，则需要在本地安装Jekyll。[Jekyll Tips](http://jekyll.tips)上有详细的教程，对我帮助很大。


一个基于Jekyll网站的目录结构通(File Structure)常如下:

```
.
├── _config.yml
├── _drafts
|   ├── begin-with-the-crazy-ideas.textile
|   └── on-simplicity-in-technology.markdown
├── _includes
|   ├── footer.html
|   └── header.html
├── _layouts
|   ├── default.html
|   └── post.html
├── _posts
|   ├── 2007-10-29-why-every-programmer-should-play-nethack.textile
|   └── 2009-04-26-barcamp-boston-4-roundup.textile
├── _site
├── .jekyll-metadata
└── index.html
```
（截自[官网](http://jekyllcn.com/docs/structure/)）

官网上对其有详细的解释，这里不再赘述。将Github Pages的repo按上述结构组建好后，Github Pages会自动解析然后生成Jekyll网页。我所需要做的工作则是在`_posts/`中添加自己的Markdown形式的博客，Jekyll就会帮我生成相对应的html网页。这些网页会被储存在`_site/`中，但是repo里并不会显示该文件夹。

基本的设置完成后，我开始寻找一些美观的Jekyll Themes，想让自己的博客看起来更赏心悦目一些。最终决定使用的是由Michael Rose制作的[HPSTR](https://mademistakes.com/work/hpstr-jekyll-theme/)。该Theme不仅提供美观的前端设置，也包含了许多可以自己customize的内容。

以上工作完成后便将之前在Wordpress上的两篇博客转移过来，用Markdown形式修改保存后放在`_posts/`，push到repo中。

至此，利用Jekyll在Github Pages上搭建静态博客网站的所有工作全部完成。接下来就需要在README里做一些reference和credit的工作。