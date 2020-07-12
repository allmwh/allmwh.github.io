---
layout: post
title: "股票當沖cp值比較，不同股價，不同檔數即可回本"
description: "股票當沖cp值比較，不同股價，不同檔數即可回本"
categories: [生活,投資]
---

先講結論，如果我沒算錯的話，**股價在100-230的個股**(不包含etf)，只要**股價跳兩檔(2 tick)**，就能賺到券商給的退佣和價差了

**僅供參考，不負任何投資上損失的責任，也不保證計算結果是對的**

<!--more-->
## 跳動檔位的不同
為什麼是100-230?，因為"不同股價，跳動的單位不同"，如下圖，圖片取自[wantgoo.com](https://m.wantgoo.com/Blog/Article/Content?BlogName=203664&ArticleID=59)

![01](/attachments/2020-07-02-day-trade-tick-compair/01.jpg)

## 檔位與價格關係圖
按照不同股價跳動檔位，與買賣股票所需要的手續費去計算，可以得到股價與檔位的關係圖，橫坐標是股價，縱座標是要幾檔回本

![02](/attachments/2020-07-02-day-trade-tick-compair/02.png)

大該在100-230是圖中最低的地方，也就是在這價位的股價，最多只要2 tick，就可以回本，賺倒退佣與差價

附上互動式的網頁及程式碼，有需要可以參考一下

## 互動網頁與原始碼
### 網頁:<https://bit.ly/2CoM67E>
<iframe
        frameborder="no"  
        style="width:100%; max-width:700px; height:400px; margin:0 auto; overflow:hidden; display:block;"
        src="/attachments/2020-07-02-day-trade-tick-compair/site.html">
      </iframe>
游標移上去，可以看到4個數字
* price:股價
* start_make:要幾檔才賺，小數點的話就進位，這裡賺錢是指，你賺到買賣所付出的所有手續費，不考慮退佣
* h_fee:買賣所包含的所有手續費(不包含券商折扣)，為了方便計算，賣出價格我設定與買入一樣，所以賣高手續費應該會多一些
* back_fee:券商退佣多少錢，我超奈米戶，券商只給我65折，可以自己改程式碼

### 程式碼:<https://git.io/JJOJv>
需要[plotly](https://plotly.com/python/)套件，有任何問題或錯誤都可以跟我說

## 勸世
當沖...，賺的慢，輸的快，不要相信網站上說得很好賺錢，當沖雖不用本，操作上還是要本，心態才不會動不動就爆炸，目前我沖算下來都賠錢拉，所以也不打算做了，高槓桿不是每個人都能承受，我就是不能承受的那個。
