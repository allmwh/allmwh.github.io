---
layout: post
title: 幫jekyll加上likecoin
description: 幫jekyll加上likecoin
categories: [jekyll]
---
之前在wordpress也有放likecoin的按鈕，透過加一些程式碼，也可以在jekyll實現

<!--more-->
## 加入代碼
### 程式碼
已經[有人](https://pingu.moe/2020/01/integrate-likebutton-with-jekyll/)幫我們寫好代碼了，也有詳細的原裡介紹

以下代碼存成`.html`檔，放在想放的地方，我是放在`_includes`中

```
<h2>請幫我按個讚</h2>
      <iframe
        frameborder="no"  
        style="width:100%; max-width:364px; height:180px; margin:0 auto; overflow:hidden; display:block;"
        src="https://button.like.co/in/embed/{{site.liker_id}}/button?referrer={{ page.url | absolute_url | cgi_escape }}">
      </iframe>

```
`<h2>請幫我按個讚</h2>`可以依自己想要顯示的文字更改，而`max-width:364px; height:180px` 是like coin工具的大小，可以自己設定，但比例盡量維持在364/180，不然會有捲動視窗醜醜的



### 插入頁面

先找到你想要插入的地方寫入以下代碼，以我為例，我只想讓他在文章中出現，所以就插在`_layouts/post.html`中

{% raw %}
```
{% if site.liker_id %}
    <div class="like-bottom">
      {% include like-bottom.html %}
    </div>
{% endif %}
```
{% endraw %}

我也與[設定jekyll開啟連結都使用新分頁開啟](https://blog.allmwh.org/2020-02/jekyll-always-newtab/)一樣，可以在`_config.yml`設定自己的likecoin id

### 寫入`_config.yml`
在`_config.yml`中插入以下代碼
```
# LikeButton
liker_id: allmwh0103
```
`liker_id`請替換成自己的like coin id 

這樣就可以了~ 效果如本頁下方的按鍵，可以的話，也幫我按個like哦~~

## 參考資料
* 給Jekyll加上LikeButton賺錢錢: [https://pingu.moe/2020/01/integrate-likebutton-with-jekyll/](https://pingu.moe/2020/01/integrate-likebutton-with-jekyll/)
* css iframe边框去掉: [https://www.cnblogs.com/ostrich-sunshine/p/8258077.html](https://www.cnblogs.com/ostrich-sunshine/p/8258077.html)

