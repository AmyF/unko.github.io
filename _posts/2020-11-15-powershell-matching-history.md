---
layout: post
title: Windows PowerShell按上方向键匹配历史记录
date: 2020-11-15 20:15 +0800
---

## 太长不看版

复制下面的命令直接运行。

```powershell
ni -Type File -Path $PROFILE
sc -Path $PROFILE -Value '
Set-PSReadLineOption -HistorySearchCursorMovesToEnd
Set-PSReadlineKeyHandler -Key UpArrow -Function HistorySearchBackward
Set-PSReadlineKeyHandler -Key DownArrow -Function HistorySearchForward
'
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

然后重启Windows PowerShell窗口。

## 步骤解释

### 创建PS的Profile文件

如果没有使用过PS相关的功能，Profile文件应该是没有的。下面是创建命令

```powershell
# ni是New-Item的缩写
# $PROFILE是系统提供的PROFILE地址
ni -Type File -Path $PROFILE
```

### 写入命令

打开Profile文件写入下列命令

```powershell
Set-PSReadLineOption -HistorySearchCursorMovesToEnd
Set-PSReadlineKeyHandler -Key UpArrow -Function HistorySearchBackward
Set-PSReadlineKeyHandler -Key DownArrow -Function HistorySearchForward
```

### 脚本权限控制

一般默认的用户权限是Undefined，是没有办法执行脚本文件的。

我们需要通过设置更高的权限来运行我们的脚本。

```powershell
# 通过该命令查看我们当前用户（CurrentUser）的权限
Get-ExecutionPolicy -List
# 通过该命令设置当前用户的权限
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

这是权限相关的文档。
https://docs.microsoft.com/zh-cn/powershell/module/microsoft.powershell.core/about/about_execution_policies

### 最后

重启PowerShell窗口，或者打开新的。
