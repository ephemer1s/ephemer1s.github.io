---
title: 在最终幻想14中进行自动化生产
cover: https://s1.imgpp.com/2021/11/23/xiv1.png
date: 2021-11-23 17:31:28
updated:
tags: 
 - FFXIV
 - ahk
 - macro
categories: 狒狒|FFXIV
keywords:
description: '一个简单的工匠脚本，基于AutoHotKeys，适用于40-60级的伊修加德收藏品'
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

## 在FFXIV中运行Autohotkey
FFXIV没有脚本检测，ban主要来源是举报导致的封禁。而AutoHotKey所执行的script语言本质上和某技的键盘宏/鼠标宏是一致的实现。尽管如此，搓脚本的时候**不要试图在人多的地方嚣张**。
大部分游戏对于按键的输入由最底层的代码实现，FFXIV也不例外，因此在FFXIV中运行Autohotkey并模拟按键输入需要使用最底层的`ControlSend()`函数，并且需要以**管理员权限**运行脚本。

💡搓脚本前检查list：
* 设置正确的loop数量，购买相应的原材料
* 背包留出足够容纳收藏品的空间
* 修理工匠装备，使用耐久度消耗降低的药水
* 检查并设置息屏时间

## 代码
### 使用脚本进行循环
工匠制造循环代码，适用于40s以内的制造宏：

```
$1::
    Loop, 35
    {
        ControlSend, ahk_parent, {Numpad0}, ahk_exe ffxiv_dx11.exe
        Sleep 1000
        ControlSend, ahk_parent, {Numpad0}, ahk_exe ffxiv_dx11.exe
        Sleep 1000
        ControlSend, ahk_parent, {Numpad0}, ahk_exe ffxiv_dx11.exe
        Sleep 2000
        ControlSend, ahk_parent, {F1}, ahk_exe ffxiv_dx11.exe
        Sleep 40000
    }
Return
```
### 使用宏进行收藏品制作
制造宏，放置于热键栏`F1`位置，适用于能工巧匠40-60级的伊修加德收藏品制作：
```Macro
手法有问题，暂时删除
```

## 原理

### ControlSend 函数

经测试，运行FFXIV时Send/SendPlay函数均不能模拟键盘输入。而[ControlSend](https://wyagd001.github.io/zh-cn/docs/commands/ControlSend.htm)可以实现相应功能。

## 相关文档
AutoHotKey中文文档：[Docs](https://wyagd001.github.io/zh-cn/docs/)
AutoHotKey英文文档：[Docs](https://www.autohotkey.com/docs/)



距离EndWalker还有两周，速速把全职业练到80级，然后去赚鬼佬的钱吧！

![xiv1.png](https://s1.imgpp.com/2021/11/23/xiv1.png)