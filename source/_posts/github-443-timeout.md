---
title: 'git push出现443: Timed out的问题与解决方案'
date: 2021-10-16 14:16:03
updated:
tags: 
 - hexo 
 - git
categories: debug record
keywords:
description:
top_img:
comments:
cover: /img/bg_default_w.png
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

# Bug Description

## Logs

报错指令

```bash
$ hexo d
```

报错信息

```
fatal: unable to access 'https://github.com/ephemer1s/ephemer1s.github.io/': Failed to connect to github.com port 443: Timed out
FATAL {
  err: Error: Spawn failed
      at ChildProcess.<anonymous> (D:\Documents\github-pages\node_modules\hexo-util\lib\spawn.js:51:21)
      at ChildProcess.emit (node:events:390:28)
      at ChildProcess.cp.emit (D:\Documents\github-pages\node_modules\cross-spawn\lib\enoent.js:34:29)
      at Process.ChildProcess._handle.onexit (node:internal/child_process:290:12) {
    code: 128
  }
} Something's wrong. Maybe you can find the solution here: %s https://hexo.io/docs/troubleshooting.html
```

## Environment

* 使用v2ray全局代理，或使用v2ray PAC代理，均报错
* GitHub仓库可以正常访问
* 禁用代理，GitHub仓库无法访问，Bug仍存在

# Solution

## Works for me

在项目根目录执行：

```bash
$ git config --global --unset http.proxy
$ git config --global --unset https.proxy
```

注：git使用https所以其实主要是第二行

## Other possible

### 刷新dns缓存

执行：

```bash
$ ipconfig /flushdns
```

注：该命令无法在项目根目录的控制台上直接执行

### 更改hosts文件

hosts文件路径：

```
C:\windows\system32\drivers\etc\hosts
```

向其中添加GitHub解析的IP，或将已添加的IP注释掉，个人感觉不靠谱。



