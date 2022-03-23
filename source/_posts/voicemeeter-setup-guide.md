---
title: "直播串流时voicemeeter的配置"
cover: https://vb-audio.com/Voicemeeter/VoicemeeterAudioMixer.jpg
date: 2021-12-03 14:46:08
updated:
tags: 
 - game
 - misc
categories: 杂学|Misc
keywords: Voicemeeter
description: 关于在使用bilibili或者t台给朋友直播的时候如何不把朋友在语音里的声音也录进去的一些声音输入输出配置的原理和可用的归档
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



## UI

![image-20211203145039655.png](https://s1.imgpp.com/2022/02/01/image-20211203145039655.png)

## 输入端

* 硬件输入 (Own Mic)

* 虚拟输入 (VAIO)

## VAIO

* VAIO (相当于OUT1)
* VAIO AUX (相当于OUT2)

## 输出



* 硬件输出 - A1 (耳机)

* 虚拟输出 - OUT1/OUT2

## IO逻辑

OBS应捕获的声音：除开黑啦以外的所有声音

耳机应捕获的声音：所有声音


大概是这样的输入输出逻辑

![image-20211203150344947.png](https://s1.imgpp.com/2022/02/01/image-20211203150344947.png)



Q：怎么在per app上指定输出设备

A：感觉是先指定默认的为VAIO 再把qq和开黑啦改成AUX