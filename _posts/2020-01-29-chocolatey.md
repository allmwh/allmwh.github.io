---
layout: post
title: windows上的軟體管理工具-chocolatey
description: windows上的軟體管理工具-chocolatey
categories: [資訊,windows,軟體小技巧]
---

chocolatey就和某些linux distribution中的軟體管理工具一樣(apt/yum)，可以集中式管理軟體的下載，安裝和移除，如果習慣linux上抓軟體的方法的話，使用這款工具在windows上會方便很多

<!--more-->

## 安裝

官網安裝教學：[https://chocolatey.org/install](https://chocolatey.org/install)

chocolatey是使用windows中的powershell安裝，在**開始中搜尋powershell**，並**右鍵以系統管理員**執行，輸入**Set-ExecutionPolicy AllSigned**或是**Set-ExecutionPolicy Bypass -Scope Process**解除一些系統上的限制，並用**Get-ExecutionPolicy**，確認一下

```
PS C:\WINDOWS\system32> Set-ExecutionPolicy AllSigned
執行原則變更
執行原則有助於防範您不信任的指令碼。如果變更執行原則，可能會使您接觸到 about_Execution_Policies 說明主題 (網址為
https:/go.microsoft.com/fwlink/?LinkID=135170) 中所述的安全性風險。您要變更執行原則嗎?
[Y] 是(Y)  [A] 全部皆是(A)  [N] 否(N)  [L] 全部皆否(L)  [S] 暫停(S)  [?] 說明 (預設值為 "N"): a

PS C:\WINDOWS\system32>  Get-ExecutionPolicy
AllSigned
```

Get-ExecutionPolicy顯示為**AllSigned**或**Bypass**就可以了

再來就鍵入以下指令，讓他跑，安裝即完成

```
Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
```

## 使用

只需開啟powershell或cmd(系統管理員身份)，輸入chocolatey的指令就可以了，常用指令如下

安裝軟體： choco install “軟體名”

移除軟體： choco uninstall “軟體名”

更新全部軟體：choco upgrade all

列出以安裝的軟體：choco list –local-only

上面的軟體名，可以在[chocolatey](https://chocolatey.org/)中官網搜尋，基本上我用的指令也就這些，當然他還有很多功能，例如他也可以自訂軟體源之類的，詳細的指令就去看[他的文檔](https://chocolatey.org/docs#usage-commands)吧

