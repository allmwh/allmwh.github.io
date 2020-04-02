---
layout: post
title: "prismjs讓jekyll程式碼區塊高亮"
description: "prismjs讓jekyll程式碼區塊高亮"
categories: [jekyll]
---

程式碼區塊語法高亮(Syntax highlighting)就是像這樣，可以依照特定的程式語言標示不同顏色，透過`prismjs`就可以自動幫我們高亮了

```python
print('this is a python code^^')
```
<!--more-->

## prismjs簡介及安裝
`prismjs`就是集合很多的程式碼語法高亮方式，引用到網頁中就可以簡單地使用了
> 官方網站:<https://prismjs.com/>

要安裝也很簡單，只要再官網的`Download`裡面，勾選你之後會用到的程式語法和Plugins，下載`js`及`css`引入html裡面即可，Plugins等等來講幾個我有用的，先稍微講一下jekyll要怎麼引入

### 在jekyll中引入`js`與`css`
下載完的`prism.js`及`prism.css`依照你的習慣放到jekyll網頁資料夾裡，我是這樣放
```
prism.js  /assets/js/prism.js
prism.css /assets/css/globals/prism.css
```
然後在`footer.html`中引入這兩個檔案，安裝就完成了
```html
<script src="/assets/js/prism.js"></script>
<link rel="stylesheet" href="/assets/css/globals/prism.css">
```

## 使用prismjs
在寫文章的時候，markdown的程式碼區塊是三個反引號```，只要在反引號旁加上程式語言名稱，`prismjs`就會依照設定的去高亮

![01](/attachments/2020-04-02-prismjs-in-jekyll/01.png)

上面出來的結果就是一開始的範例，當然不只python，要javascript、html、ruby等程式語法都可以，他也支援bash或powershell等command line

## 小工具Plugins
有沒有注意到我的高亮區塊上面有按鈕，透過Plugins就可以實現了

![02](/attachments/2020-04-02-prismjs-in-jekyll/02.png)

prismjs網頁上的Plugins有這些，這邊介紹幾個我摸過的

![03](/attachments/2020-04-02-prismjs-in-jekyll/03.png)

### Copy to Clipboard Button
就是可以貼到剪貼版裡~~，安裝很簡單，就是我現在有的樣式，勾起來引入`css`和`js`就自動實現了

### Show Language
顯示目前的程式語言，markdown中設什麼語言就顯示什麼語言

### Line Numbers
顯示行數，不過這無法直接在markdown中直接打出來，要寫html才行，可以參考他網頁的說明和github原始碼，或是我這篇文章的`.md`檔
>官方說明:<https://prismjs.com/plugins/line-numbers/>
> 
>官方github範例:<https://git.io/Jvdb6>
> 
>我的.md:<https://git.io/Jvdb5>

<pre class="language-none line-numbers"><code>This raw text is not highlighted
but it still has
line numbers</code></pre>

### Command Line
這也蠻酷的，貼bash指令的時候可以標示出`root@localhost`的標籤，頗好看，不過這也要html，一樣給參考連結
>官方說明:<https://prismjs.com/plugins/command-line/>
>
>官方github範例:<https://git.io/Jvdbi>
>
>我的.md:<https://git.io/Jvdb5>

裡面的`root`、`localhost`、或是user標示`#`都可以自己設定

<pre class="command-line" data-user="root" data-host="localhost" data-output="3-10"><code class="language-bash" >cd ~/
ls -la
drwxr-xr-x 2 root root      4096  1月 26 20:38 下載/
drwxr-xr-x 2 root root      4096  1月 26 20:38 公共/
drwxr-xr-x 2 root root      4096  1月 26 20:38 圖片/
drwxr-xr-x 2 root root      4096  1月 26 20:38 影片/
drwxr-xr-x 2 root root      4096  1月 26 20:38 文件/
drwxr-xr-x 2 root root      4096  1月 28 01:03 桌面/
drwxr-xr-x 2 root root      4096  1月 26 20:38 模板/
drwxr-xr-x 2 root root      4096  1月 26 20:38 音樂/</code></pre>

- - -
要貼`html`的地方，看官方文件或我的md應該都能了解，不懂的話可以問我，只有要高亮的話，設定下來應該算是簡單，又能有好看的程式碼~~

