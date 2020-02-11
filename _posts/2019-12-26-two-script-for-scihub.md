---
layout: post
title: 兩個輔助sci-hub的腳本
description: sci-hub在瀏覽器上的輔助腳本，讓sci-hub更好用
categories: [資訊,chrome,軟體小技巧,研究所]
---

sci-hub應該不少人都知道，就是可以不用透過學校vpn來下載文獻的東西(學校沒買期刊的話，vpn還不一定有用…)，這樣的方式似乎不太合法xd，不過為了畢業、為了boss，還是別管那麼多吧…， 這邊**介紹兩個腳本給chrome或firefox用**，使用sci-hub會方便許多

<!--more-->

## sci-hub簡介

若很長在搜尋文獻的話，有些文獻需要…錢，所以這就是為啥有時下載期刊，需要透過vpn連到學校網路才能看，期刊網站會認學校的ip，好在我們有[scu-hub](https://sci-hub.tw/)，這網站聽說也蠻辛苦的，到處被抓，所以一直換網址xd，而一般我們在用sci-hub的用法是:發現想看的文獻不能下載，就把網址(不管是pubmed還是期刊網站)貼過去sc-hub的搜尋框，然後就會蹦出文獻了

## 安裝tampermonkey

先在瀏覽器上安裝**tampermonkey**，看是什麼瀏覽器，按一按安裝
[chrome](https://chrome.google.com/webstore/detail/tampermonkey/dhdgffkkebhmkfjojejmpbldmpobfkfo?hl=zh-TW)
[firefox](https://addons.mozilla.org/zh-TW/firefox/addon/tampermonkey/)

## 文獻的下載按紐-Sci-hub button

安裝完tampermonkey後，再到[Sci-hub button](https://greasyfork.org/zh-TW/scripts/370246-sci-hub-button)下載腳本，一樣也是很懶人的安裝，安裝完，之後你查文獻的時候，可以下載的話就會出現一個黃色按鈕讓你下載了

## 去掉sci-hub的側邊欄

sci-hub打開後會有像這樣的側邊欄，再裝一個腳本，就可以把它去掉了!

![圖片_007](/attachments/2020-12-26-two-script-for-scihub/圖片_007.png)

[Remove annoying boxes from Sci-Hub](https://greasyfork.org/zh-TW/scripts/28331-remove-annoying-boxes-from-sci-hub)，安裝後，需要修改sci-hub的網址，不然腳本是不會觸發到的，打開tampermonkey的控制台，chrome的話在右上角可以按

<img src="/attachments/2020-12-26-two-script-for-scihub/圖片_010-1.png" alt="圖片_010-1" style="zoom:67%;" />

找到Remove annoying boxes from Sci-Hub，並編輯

![圖片_008-3](/attachments/2020-12-26-two-script-for-scihub/圖片_008-3.png)

在第4行有include啥的，將那行改成下面那樣，再存檔

```
// @include  https://*sci-hub.tw/*
```

![圖片_009-2](/attachments/2020-12-26-two-script-for-scihub/圖片_009-2.png)

這樣之後連sci-hub的時候，就不會看到那個側邊框了哦