---
layout: post
title: "用docker compose使用resilio sync"
description: "用docker compose使用resilio sync"
categories: [docker,Linux]
---

docker+compose真的頗方便，一些系統的相依問題都能不管他，嘗試使用了docker在linux(Ubuntu)下來佈建`resilio sync`，resilio sync是分散式的檔案同步軟體，介紹可以看[這邊](https://mobileai.net/2017/02/13/resilio-sync/)

<!--more-->
## docker、docker compose 安裝
### docker
以root身分執行，在shell中鍵入以下指令
```
curl -fsSL https://get.docker.com -o get-docker.sh && sh get-docker.sh

usermod -aG docker root

systemctl enable docker ; systemctl start docker
```
### docker compose
```
curl -L "https://github.com/docker/compose/releases/download/1.25.5/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

chmod +x /usr/local/bin/docker-compose
```
## resilio 安裝
可以到官方的github下載compose file: <https://git.io/JfsOm> ，或是直接改我的，複製下來後檔名存成`docker-compose.yaml`，可以開一個資料夾存compose file和一些resilio的設定檔
```yaml
version: '3'

services:
  resilio_sync:
    image: resilio/sync
    restart: always
    ports:
     - 127.0.0.1:9999:8888
     - 55555:55555/tcp
     - 55555:55555/udp     
    volumes:
     - /nosync/resilio_sync_data:/mnt/sync/folders/resilio_sync_data      
     - /nas:/mnt/sync/folders/nas
     - ./config:/mnt/sync/config

```
有些地方需要自己改一下
* `restart`:要不要自動重開container，`always`就會自動重開，不想自動重開的話把那行刪掉
  
* `ports`: 之後管理server的port，預設是不會bind到網路上的，只有localhost可以用，如果想要區網電腦可以進去管理的話，請把那行改成`- 8888:8888`
  
* `volumnes`: 設定你要讓resilio sync存取的資料夾，就是我volume中的前兩行，我用的時候有發現在**container中的路徑一定要在**`/mnt/sync/folders/`**後面**，resilio sync才讀的到
  
  ```yaml
  - /nosync/resilio_sync_data:/mnt/sync/folders/resilio_sync_data
  - /server上的路徑:/mnt/sync/folders/`container`中要顯示的路徑
  ```
  `- ./config:/mnt/sync/config`就是resilio sync的設定檔，預設存在當前資料夾中

## 啟動 resilio sync
上面都設定好之後，就可以來打開了，當前資料夾下鍵入

```
docker-compose up -d
```

`-d`是讓container背景執行，開好之後到瀏覽器下輸入`電腦ip:8888`，就可以使用

一些可能會用到的compose指令:
* 關掉container: docker-compose down
* 重開container: docker-compose restart

## 可能會遇到的問題
列一下可能會出現的問題
* `電腦ip:8888`連不上
  * compose file沒有設定好，port中的設定`- 127.0.0.1:9999:8888`要改成`- 8888:8888`
  * 有防火牆，ubuntu是用`ufw`，centos則是`firewalld`，關鍵字去搜一下就能解決
  * SElinux擋住了，不想搞policy的話，我都直接關掉，可以看之前寫的[文章](https://blog.allmwh.org/2019-05/wordpress-update-issue-centos7/)
                   
* resilio sync裡面沒有出現我想同步的資料夾
  * `volumnes`沒有設好，記得在container裡面的掛載位置要在`/mnt/sync/folders/`後面
                    
* 忘記resilio sync密碼
  * 參考[官方說明](https://help.resilio.com/hc/en-us/articles/205450295-How-do-I-reset-my-WebUI-password-)，把`./config`中的`settings.dat`和`settings.dat.old`刪掉即可

