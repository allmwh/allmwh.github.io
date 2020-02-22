---
layout: post
title: 設定jekyll開啟連結都使用新分頁開啟
description: 設定jekyll開啟連結都使用新分頁開啟
categories: [jekyll]
---

在搞jekyll的時候，發現發現**開超連結都沒辦法開新分頁**，可以**透過加一些程式碼**，讓所有的非網域內的網址都用超連結開

<!--more-->

## 修改教學

### 新增一個.js檔案

檔案可以直接下載: <a href="/attachments/2020-02-15-jekyll-always-newtab/new-tab.js" download="new-tab.js">new-tab.js</a>

或是複製以下代碼，我是放到 `/asset/js/new-tab.js`

```
function handleExternalLinks () {
    var host = location.host
    var allLinks = document.querySelectorAll('a')
    forEach(allLinks, function (elem, index) {
      checkExternalLink(elem, host)
    })
  }
  
  function checkExternalLink (item, hostname) {
    var href = item.href
    var itemHost = href.replace(/https?:\/\/([^\/]+)(.*)/, '$1')
    if (itemHost !== '' && itemHost !== hostname) {
      item.target = '_blank'
      item.rel = 'noopener noreferrer'
    }
  }
  
  // NodeList forEach function
  function forEach (array, callback, scope) {
    for (var i = 0; i < array.length; ++i) {
      callback.call(scope, array[i], i)
    }
  }
  
  handleExternalLinks ()
```

代碼我也是參考別人的，簡單來說就是會找出所有非本網域內的超連結，加上下面兩個值

`target="_blank"` 代表**開啟新分頁**，有這個值就可以開新分頁了

`rel="noopener noreferrer"`算是**讓超連結變的更安全**，預防網站**被釣魚軟體注入**，詳細可以看一下參考資料，有蠻有趣的[範例網頁](http://keenwon.com/demo/201603/noopener.html)讓你知道兩者的差別

### 代碼插到網頁上

將`new-tab.js`代碼引用到網站裡，我是放到`_include/footer.html`，複製以下代碼插入

{% raw %}
```
<!-- new-tab.js -->
{% if site.new-tab.enable %}
  <script type="text/javascript" src="/assets/js/new-tab.js"></script>
{% endif %}
```
{% endraw %}

並且**用if做了一個開關**，方便我們在`_config.yml`，決定要不要開啟這個功能

### 修改_config.yml

打開`_config.yml`，複製以下代碼插入

```
#連結自動開新分頁
new-tab:
  enable: true
```
只要將`enable`設置成`true`，開啟新分頁的功能就會被打開，這樣就設定完成了~

## 參考資料
* Jekyll 新分頁開啟超連結:[https://note.pcwu.net/2017/02/05/jekyll-link-new-tab/](https://note.pcwu.net/2017/02/05/jekyll-link-new-tab/)

* 使用rel=noopener:[http://keenwon.com/1548.html](http://keenwon.com/1548.html)

* 有無noopener的差別demo: [http://keenwon.com/demo/201603/noopener.html](http://keenwon.com/demo/201603/noopener.html)

