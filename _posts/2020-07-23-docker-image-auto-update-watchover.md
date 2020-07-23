---
layout: post
title: "自動更新docker的image-watchover"
description: "自動更新docker的image-watchover"
categories: [docker,linux]
---

docker可以很快部屬所需的服務，更新或刪除也都很方便，但如果抓的image的**tag**是**latest**的話，docker不會自動幫你更新image，可以透過**watchtower**這個container幫我們監控image有沒有新的，自動抓新的image下來，並重新佈署container

> repo:<https://github.com/containrrr/watchtower>
<!--more-->

## watchtower的compose file
還是喜歡用docker-compose做，照下面打就可以了
<pre class="language-yml line-numbers"><code>version: "3.3"
services:
 watchtower:
  container_name: watchover
  image: containrrr/watchtower
  volumes:
   - /var/run/docker.sock:/var/run/docker.sock
   - /etc/timezone:/etc/timezone:ro
  environment:
   - WATCHTOWER_SCHEDULE=0 0 3 * * *</code></pre>

## 檢查更新週期
### 固定時間執行
上述範例是在每天凌晨3點檢查image的更新，可以自己修改，watchover使用[cron的6位數版本](https://pkg.go.dev/github.com/robfig/cron@v1.2.0?tab=doc#hdr-CRON_Expression_Format)，有六位數，分別代表的就是: **秒 分 小時 天in月 月 天in周**，上面就代表在3點0分0秒，且每天執行(*代表每個單位都執行)
### 隔一段時間執行
除了設定固定時間，也可以設成隔多少時間就執行一次
<pre class="language-yml line-numbers"><code> environment:
   - WATCHTOWER_POLL_INTERVAL=300</code></pre>
上面代表每隔300秒會執行一次，但我測試之後，好像數值太大會不能執行，要試一下

## 特定container不自動更新
這個container開起來後，電腦上的container都會被檢查更新，但有些container自動更新服務可能就跑不起來了，可以在不想自動更新的container設定中加上**com.centurylinklabs.watchtower.enable=false**
<pre class="language-yml line-numbers"><code>version: "3.3"
services:
  web:
    image: web
    labels:
      - "com.centurylinklabs.watchtower.enable=false"</code></pre>

## 執行狀況
設定好了後，放幾天查看log，看起來有正常運作了
<pre class="language-shell"><code>docker container logs watchover</code></pre>
![01](/attachments/2020-07-23-docker-image-auto-update-watchover/01.png)

也可以看一下他的**[文檔](https://containrrr.dev/watchtower/)**，找自己需要的功能

> 文檔:<https://containrrr.dev/watchtower/>
