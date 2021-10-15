---
title: Hexo博客正确安装Sagiri主题的两个额外步骤
date: 2021-10-16 01:04:20
updated:
tags: hexo
categories: 
keywords:
description:
top_img:
comments:
cover:
toc:
toc_number:
copyright:
copyright_author:
copyright_author_href:
copyright_url:
copyright_info:
mathjax:
katex:
aplayer:
highlight_shrink:
aside:
---
正常情况下使用hexo主题只需在`./themes`文件夹下使用`git clone`即可，但在使用[sagiri主题](https://github.com/DIYgod/hexo-theme-sagiri)时遇到了无法正常显示的问题，经检查，使用该主题相比普通hexo主题需要两个额外的步骤。

# 安装主题所需的依赖

cd到sagiri主题目录，在该目录下打开控制台，使用命令：

```
$ npm install
```

即可安装全部所需package



# 安装`hexo-renderer-swig`包

安装全部依赖后生成hexo，打开本地主页，无法正常显示，并出现`“ {% extends ‘_layout.swig‘ %} {% import ‘_macro/post.swig‘ as post_template %}“`问题。原因是hexo>=5.0版本下swig包需要自行安装，在hexo根目录执行命令如下：

```
$ npm install hexo-renderer-swig
```

之后，即可使用hexo命令顺利初始化sagiri主题的博客环境。

------

PS:虽然最后还是用了butterfly而不是sagiri，但是DIY佬的html画pixiv图标还是有震撼到我。。。
