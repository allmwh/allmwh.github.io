---
layout: post
title: 用chrome網址搜尋查字典-自訂搜尋引擎
description: 用chrome網址搜尋查字典-自訂搜尋引擎
categories: [chrome]
---

我猜標題這樣下可能沒人知道這在幹嘛，直接展示一遍好了～

<!--more-->

## 範例：英英字典

以[Oxford Learner’s Dictionary](https://www.oxfordlearnersdictionaries.com/)當作範例

![01-2](/attachments/2020-01-15-google-custom-search-engine/01-2.gif)

知道我的意思了嗎～～ 只要在chrome的網址列上打想查的單字，就可以直接連到指定的網站查了

## 範例：google學術搜尋

利用[google學術搜尋](http://scholar.google.com.tw/)，要找論文一樣可以哦

![02-1](/attachments/2020-01-15-google-custom-search-engine/02-1.gif)

## 範例：stack overflow

要去[stack overflow](https://stackoverflow.com/)去問[怎麼退出vim](https://gitbook.tw/chapters/command-line/vim-introduction.html)也可以的…

![03](/attachments/2020-01-15-google-custom-search-engine/03.gif)

總之，只要有可以搜尋功能的網頁，都可以自訂搜尋引擎來快速搜尋哦

## 觀察一下網址吧

首先打開你想要設的網站，我用[google 學術搜尋](https://www.oxfordlearnersdictionaries.com/)舉例，我搜尋[p53](https://zh.wikipedia.org/zh-tw/P53)，網址長這樣

```
https://scholar.google.com.tw/scholar?hl=zh-TW&as_sdt=0%2C5&q=p53&oq=
```

這時試著找找你搜尋的關鍵字，像我的p53躲在＆q=p53這邊，接下來試著帶換這個字串，例如我把他換成[p21](https://en.wikipedia.org/wiki/P21)，網址就變這樣

```
https://scholar.google.com.tw/scholar?hl=zh-TW&as_sdt=0%2C5&q=p21&oq=
```

送出網址，看能不能搜尋，可以跑出結果的話代表已經找到搜尋字串的位置，把這串搜尋網址複製起來，帶換的地方也稍微記一下

## 在chrome中新增搜尋引擎

chrome設定，搜尋引擎，**管理搜尋引擎**

![Image-001](/attachments/2020-01-15-google-custom-search-engine/Image-001.png)

上方預設搜尋引擎不要管他，我們來**新增下面的其他搜尋引擎**

![Image-001-1](/attachments/2020-01-15-google-custom-search-engine/Image-001-1.png)

有3個欄位讓你填

- **搜尋引擎：**就隨便取個名字吧，對於搜尋不影響
- **關鍵字：**設定你想用這網頁搜尋時，一開始先在網址列上打的字串，以我的為例，**google學術搜尋我就設sch**
- **以 %s 取代查詢的網址** ：這邊就是將我們剛剛找到替換字串的地方，換成 **%s** ，如剛剛的google學術搜尋，網址就變成

```
https://scholar.google.com.tw/scholar?hl=zh-TW&as_sdt=0%2C5&q=%s&oq=
```

這樣就大功告成了！！，往後想搜尋什麼，只要在網址列上打東西，方便很多，外人看來應該也頗潮的吧，應該…拉，基本上所有的網址都能這樣改，如果有不知道怎麼設的，歡迎下面留言，可以幫你看看哦

