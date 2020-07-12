---
layout: post
title: "在nginx-proxy中使用Let's Encrypt，方便使用https"
description: "在nginx-proxy中使用Let's Encrypt，方便使用https"
categories: [docker]
---

[nginx-proxy](https://github.com/nginx-proxy/nginx-proxy)是docker中的image，可以很方便的把其他container的服務代理出去，而搭配[**docker-letsencrypt-nginx-proxy-companion**](https://github.com/nginx-proxy/docker-letsencrypt-nginx-proxy-companion)即可透過[Let's Encrypt](https://letsencrypt.org/)，將網站很懶人的加上https憑證

<!--more-->

## nginx-proxy的compose file
安裝很簡單，參考我docker-compose的範例

<pre class="language-none line-numbers"><code>version: "3.3"
 nginx-proxy:
  container_name: nginx-proxy
  image: jwilder/nginx-proxy:latest
  ports:
   - 80:80
   - 443:443
  volumes:
   - /var/run/docker.sock:/tmp/docker.sock:ro
   - nginx_certs:/etc/nginx/certs 
   - nginx_vhost.d:/etc/nginx/vhost.d
   - nginx_html:/usr/share/nginx/html
  restart: always
 
 nginx-proxy-letsencrypt:
  container_name: nginx-proxy-letsencrypt
  image: jrcs/letsencrypt-nginx-proxy-companion
  volumes:
   - /var/run/docker.sock:/var/run/docker.sock:ro
   - nginx_certs:/etc/nginx/certs
   - nginx_vhost.d:/etc/nginx/vhost.d
   - nginx_html:/usr/share/nginx/html
  environment:
   - DEFAULT_EMAIL=jonas870103@gmail.com
   - NGINX_PROXY_CONTAINER=nginx-proxy
  restart: always

volumes:
 nginx_certs:
 nginx_vhost.d:
 nginx_html:</code></pre>

`2-13`行為**nginx-proxy**的設定，除了原本的格式外，需要加上
* 第`7`行的port，需打開`443`，讓https過
* 第`10-12`行的volume，這就是https會用到的檔案，待會會跟 **letsencrypt-nginx-proxy-companion**共用volume

`15-26`行為letsencrypt-nginx-proxy-companion，負責幫我們產生ssl憑證
* 第`18-22`行可以照貼，就是會跟**nginx-proxy**共用volume，產生完憑證丟給他用
* 第`24`行可以改成自己的email，這樣網站憑證快要過期的時候會通知你，不過這個container也會幫你自動更新的

`28-31`即為用了哪些volumes，docker-compose規定要這樣寫

至此proxy端的compose皆設定完成

## 服務範例-jellyfin

[jellyfin](https://jellyfin.org/)是免錢版的[emby](https://emby.media/)，可以丟你喜歡的音樂或影片，透過網頁或app打開，改天再來寫一篇關於jellyfin的

![01](/attachments/2020-07-12-nginx-proxy-letsencrypt-in-docker/01.jpg)

compose file如下
<pre class="language-none line-numbers"><code>version: "3.3"
services:
 jellyfin:
  image: jellyfin/jellyfin:latest
  container_name: jellyfin
  volumes:
   - /nas/music:/mnt/music:ro
   - /nas/video:/mnt/video:ro
   - ./jellyfin/config:/config
  ports:
   - 1900:1900/udp
   - 8096:8096
  environment:
   - VIRTUAL_PORT=8096
   - VIRTUAL_HOST=YOUR.URL.ORG
   - LETSENCRYPT_HOST=YOUR.URL.ORG
   - AUTO_UPDATES_ON=true
  restart: always</code></pre>

與proxy有關的設定，只有`14-16`行而已，其他的是jellyfin自己的設定，先不管他
* `14`行，設定該應用程式用到的port，**nginx-proxy**會從這個port撈資料
* `15`行，打上你想要取的url，之後在dns服務商中設定一樣的alias的話，就可以透過這網址連到服務了
* `16`行，一樣是url，如果需要https的話，就要打，**letsencrypt-nginx-proxy-companion**才會幫你認，若不需要https，打`15`行那樣就可

這樣就設定完成了，把compose打開，`docker compose up -d`試試，有https的網站，他還會自動幫你打開hsts，所有流量都會強制使用https呢