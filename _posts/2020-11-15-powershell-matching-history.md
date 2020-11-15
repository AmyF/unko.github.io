---
layout: post
title: Windows PowerShell按上方向键匹配历史记录
date: 2020-11-15 20:15 +0800
---

打开PowerShell输入命令。
```
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```
