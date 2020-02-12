---
layout: post
title: 調低surface的解析度-安裝intel的驅動程式
description: 調低surface的解析度
categories: [資訊,Windows]
---

調低surface的解析度，最近買了一台二手的surface pro 5，用起來真的不錯，很輕可以隨身帶著走，但一個小缺點就是，surface的**預設解析度好高xd**，調低解析度不僅可以**省電**一點，在遠端桌面的時候也不用**吃那麼多頻寬**，比較順

<!--more-->

## 思路

由於surface pro 5**預設解析度為2736×1824**，長寬比為1.5，windows預設沒有**1920×1280**這長寬比為1.5選項，透過**安裝intel原本的驅動程式**，自訂解析度

## 安裝intel驅動程式

surface預設是不給安裝intel原廠驅動的，但還是能安裝的，從這個網址下載pro 5的驅動
https://downloadcenter.intel.com/search?keyword=Intel+HD+Graphics+620

其他代的surface，只要知道顯卡的型號都能照做，在控制台>>裝置管理員>>顯示卡中，如下圖pro 5是620

![註解-2019-12-07-171331](/attachments/2019-12-07-change-surface-resolution/註解-2019-12-07-171331.png)

記得下載壓縮檔，不要下載exe，不然預設不會給你裝喔，下載完解壓縮，到上面的裝置管理員，選顯示卡>>右鍵更新驅動程式>>瀏覽電腦上的驅動程式軟體>>選解壓縮的資料夾，下一步就會幫你安裝了，會跑一陣子

![註解-2019-12-07-171634](/attachments/2019-12-07-change-surface-resolution/註解-2019-12-07-171634.png)

## 變更解析度

安裝完重開機，在開始中就會出現intel的設定工具，打開**intel顯示晶片控制中心**>>顯示>>在解析度那邊有個**訂製**選項，自訂解析度如下:

![註解-2019-12-07-171950](/attachments/2019-12-07-change-surface-resolution/註解-2019-12-07-171950.png)

這樣就成功降解析度了哦，跟原本相比個人認為真的沒差多少，又能省電~~