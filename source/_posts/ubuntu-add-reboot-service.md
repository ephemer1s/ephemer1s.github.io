---
title: Ubuntu系统使用Service添加开机启动项
cover: https://imgpp.com/s1/2022/03/18/image-20220317192940749.png
date: 2022-03-17 19:07:03
updated:
tags:
 - Ubuntu
 - Shell
categories: 工程|Engineering
keywords:
 - Ubuntu
 - Shell
 - Service
description:
top_img:
comments:
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



在ECE1779课程中遇到了需要设置Ubuntu开机启动项的问题，将设置开机启动项的方法记录如下。

## 1. 新建Service文件

在Ubuntu系统中，Service文件的目录是`/etc/system/systemd/`。在该目录中的Service文件在使用`systemctl`指令开启后将按其启动规则进行启动并在后台运行。

* 使用Vim新建并编辑Service文件：在etc目录下必须使用`sudo`才可以对文件进行写操作。指令为：

```bash
sudo vim /etc/system/systemd/run-memcache.service
```

* 在文件内，对service进行编辑：

```shell
[Unit]
After=network.service
Description=Test Service

[Service]
ExecStart=/bin/bash /bin/run-memcache.sh

[Install]
WantedBy=multi-user.target
```

* `:wq`保存并退出。之后，对service文件进行激活：

```bash
sudo systemctl enable run-memcache.service
sudo systemctl start run-memcache.service
```

* 由此，在重启后即可使该service自动运行`/bin/run-memcache.sh`脚本。

## 2. 使用bash脚本运行python文件

* 通过该`/bin/run-memcache.sh`脚本，可以启动虚拟环境并运行Flask服务器：

```bash
#!/bin/bash
#!/usr/bin/env python3

source '/home/ubuntu/memcache/.venv/bin/activate'
cd '/home/ubuntu/ece1779h-a1/a2'
python3 'memcacheRun.py'
```

* 在这里，似乎不需要对python3的路径进行解析。需要注意的是：当没有执行cd指令时，python文件会在系统根目录执行，其操作会对根目录产生影响（添加或删除文件）。因此必须先cd到工程目录，再运行python文件。

## 3. 查看service运行日志

使用journalctl相关指令可查询service的运行日志。指令为：

```bash
sudo journalctl -u run-memcache
```

![image-20220317192940749](https://imgpp.com/s1/2022/03/18/image-20220317192940749.png)

## 相关资料

[How To Use Systemctl to Manage Systemd Services and Units](https://www.digitalocean.com/community/tutorials/how-to-use-systemctl-to-manage-systemd-services-and-units)

[Systemctl Cheatsheet](https://access.redhat.com/sites/default/files/attachments/12052018_systemd_6.pdf)