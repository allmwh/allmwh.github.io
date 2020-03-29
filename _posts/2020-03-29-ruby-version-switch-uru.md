---
layout: post
title: "在windwos系統中切換Ruby的版本-uru"
description: "在windwos系統中切換Ruby的版本-uru"
categories: [Ruby]
---

在跑jekyll的時候，發現裝錯Ruby版本，一直Run不起來，Ruby好像還沒有像Anaconda那樣的python虛擬環境的方式，不過也有比較簡單的方法可以切換

<!--more-->

## 安裝各式版本的Ruby
Windwos的話，大家比較推的都是用[rubyinstaller](https://rubyinstaller.org/)安裝Ruby，把你會用到的版本先安裝下來

## uru安裝-使用Chocolatey 

推薦用Chocolatey安裝，沒有Chocolatey的話，可以[看這裡](https://blog.allmwh.org/2020-01/chocolatey/)，先到uru的repo下載Chocolatey安裝包

> 網址:[https://bitbucket.org/jonforums/uru/wiki/Downloads](https://bitbucket.org/jonforums/uru/wiki/Downloads)

點選`Chocolatey`，檔案名稱為`uru.x.x.x.nupkg`，下載下來後，開cmd到下載資料夾執行安裝指令
```
cd D:\Downloads #你的下載位址
choco install uru.x.x.x.nupkg #下載檔名

```
## 將ruby加到uru裡

找到Ruby的安裝資料夾，用`rubyinstaller`裝的話，預設會在C槽
![01](/attachments/2020-03-29-ruby-version-switch-uru/01.png)

記錄下路徑並加上`bin`，以我的為例，我有`Ruby24-x64`和`Ruby26-x64`兩個版本，路徑就長這樣
```
Ruby24-x64   C:\Ruby24-x64\bin
Ruby26-x64   C:\Ruby26-x64\bin
```

在`cmd`裡輸入`uru`，應該可以看到有東西跑出來
```
C:\Users\allmw>uru

uru v0.8.5
Usage: uru [options] CMD ARG...

where CMD is one of:
   TAG   use ruby identified by TAG, 'auto', or 'nil'
 admin   administer uru installation
   gem   run a gem command with all registered rubies
    ls   list all registered ruby installations
  ruby   run a ruby command with all registered rubies

for help on a particular command, type `uru help CMD`

```

分別加入Ruby到uru裡，`tag`可以幫Ruby版本取名字，方便之後切換
```
uru admin add C:\Ruby24-x64\bin  --tag 249
uru admin add C:\Ruby26-x64\bin  --tag 265

```

查看目前有的Ruby
```
uru ls
```
![02](/attachments/2020-03-29-ruby-version-switch-uru/02.png)

## 切換版本

很簡單，只要`uru 版本`，就可以了
```
uru 265
```

## 參考資料
* [How to have multiple versions of Ruby AND Rails, and their combinations on Windows?](https://stackoverflow.com/questions/3648744/how-to-have-multiple-versions-of-ruby-and-rails-and-their-combinations-on-windo)
* [uru-bitbucket](https://bitbucket.org/jonforums/uru/src/master/)
* [Ruby Version Managers](https://rubyonwindowsguides.github.io/book/ch02-03.html)




