---
layout: post
title: "ubuntu 20.04 左側應用程式可以click to minimize"
description: "ubuntu 20.04 左側應用程式可以click to minimize"
categories: [linux]
---

ubuntu左側app列打開應用程式的時候，預設是不能再按一次那個應用程式縮小的，可以把它改成與windows類似，也就是按了可以縮小(click to minimize)
<!--more-->

## 安裝dconf editor
要先裝一個應用程式**dconf editor**，給我的感覺有點像windows中的登錄檔編輯器，可以修改ubuntu中很多程式的schema(就是各種不同的設定)

```
sudo apt upgae
sudo apt install dconf-editor
```

## 更改dash-to-dock裡面的click-action
安裝好之後在應用程式裡打開**dconf編輯器**

![01](/attachments/2020-08-23-gnome-dock-apps-click-to-minimize/01.png)

直接搜尋**dash-to-dock**，出來的結果應改只有一個，或是可以慢慢點路徑進去，進去dash-to-dock，找到**click-action**
```
org -> gnome -> shell -> extensions -> dash-to-dock
```
關閉使用預設值，參數改成**minimize-or-previews**，也可以試試其他的方式，但我覺得這是與windows操作習慣最類似的
![02](/attachments/2020-08-23-gnome-dock-apps-click-to-minimize/02.png)

## 參考資料
* [Click on Icon to Minimize Application Window in Ubuntu 18.04](https://tipsonubuntu.com/2018/04/15/click-icon-minimize-application-window-ubuntu-18-04/)