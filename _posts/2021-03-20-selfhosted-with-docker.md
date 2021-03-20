---
layout: post
title: "用docker自建一堆服務，selfhosted補完計畫"
description: "用docker自建一堆服務，selfhosted補完計畫"
categories: [Linux,Docker]
---

不知不覺中，我用docker架的selfhosted服務已經這麼多了～～～
<!--more-->

![00](/attachments/2021-03-20-self-hosted-with-docker/00.png)

想用一系列文章紀錄一下我裝的東西，也怕以後忘記，之後會以一個禮拜1-2篇，介紹一下我用的一堆container，這篇先簡短介紹一下我用的一堆服務

## 怎麼找self-host軟體
一開始當然就是google了，想要用什麼工具自架，就打`什麼工具 selfhosted`就有一堆結果了，也有人整理了self-host的清單，可以直接從裡面找關鍵字
* [awesome-selfhosted](https://github.com/awesome-selfhosted/awesome-selfhosted)

## 目前用的self-host介紹
### traefik
反向代理服務器，因為有很多sef-host服務都要放網頁出去，用個反向代理工具可以很快管理，也很方便，一定得裝的
* image: [traefik](https://hub.docker.com/_/traefik)
* github:　<https://github.com/traefik/traefik>
* 介紹: 

![01](/attachments/2021-03-20-self-hosted-with-docker/01.png)

### authelia
可以與traefik做配合，當成一個traefik的`middleware`，有些服務沒有做登入的功能，就可以用這個做一個登入界面，安全更有保障，也支援兩步驟驗證
* image: [authelia/authelia](https://hub.docker.com/r/authelia/authelia)
* github: <https://github.com/authelia/authelia>
* 介紹:

![02](/attachments/2021-03-20-self-hosted-with-docker/02.png)

### anki-server
背單字軟體[anki](https://apps.ankiweb.net/)，可以自己架個同步服務器，同步很快
* image: [kuklinistvan/anki-sync-server](https://hub.docker.com/r/kuklinistvan/anki-sync-server)
* github: <https://github.com/ankicommunity/anki-devops-services>
* 介紹:

### calibre 與 calibre-web
電子書管理工具[calibre](https://calibre-ebook.com/)，可以搬到網路上用，`calibre-web`是用django寫的，有比較好看的網頁界面，`calibre`我目前看到的功能只是把桌面版calibre搬到網頁上而已，兩者可以分開使用，目前我`calibre-web`用的比較多
#### 1.calibre-web
   * image: [ghcr.io/linuxserver/calibre-web](https://hub.docker.com/r/linuxserver/calibre-web)
   * github: <https://github.com/linuxserver/docker-calibre-web>
   * 介紹:

![03](/attachments/2021-03-20-self-hosted-with-docker/03.png)

#### 2.calibre
   * image: [ghcr.io/linuxserver/calibre](https://hub.docker.com/r/linuxserver/calibre)
   * github: <https://github.com/linuxserver/docker-calibre>
   * 介紹:

![04](/attachments/2021-03-20-self-hosted-with-docker/04.png)

### filebrowser
用go寫的工具，可以把server的資料夾分享出來，放在網路上變成雲端硬碟，搜尋或下載的速度都還不錯，但在docker上設定有點不齊全就是
* image: [filebrowser/filebrowser](https://hub.docker.com/r/filebrowser/filebrowser)
* github: <https://github.com/filebrowser/filebrowser>
* 介紹:

![05](/attachments/2021-03-20-self-hosted-with-docker/05.png)

### gotify
也是用go寫的，算是一個通知管理平台，可以自己寫個程式，用他的api推通知到手機app或電腦上，應用彈性很高的程式，我現在實驗跑完也是用這個通知我XD
* image: [gotify/server](https://hub.docker.com/r/gotify/server)
* github: <https://github.com/gotify>
* 介紹:

![23](/attachments/2021-03-20-self-hosted-with-docker/23.png)

### guacamole
apache guacamole可以搭配vncserver在網頁上遠端操控電腦，包含`guacd(guacamole的daemon)`和`guacamole(網頁前端)`，，我也是用這個跑一些好久好久的實驗的＝＝
* image:
  * [ghcr.io/linuxserver/guacd](https://hub.docker.com/r/linuxserver/guacd)
  * [guacamole/guacamole](https://hub.docker.com/r/guacamole/guacamole)
* github:
  * <https://github.com/linuxserver/docker-guacd>
* 介紹:

![06](/attachments/2021-03-20-self-hosted-with-docker/06.png)

### jellyfin
跟[emby](https://emby.media/)，[plex](https://www.plex.tv/)很像，不過完全免費，可以架一個媒體伺服器
* image: [jellyfin/jellyfin](https://hub.docker.com/r/jellyfin/jellyfin)
* github: <https://github.com/jellyfin/jellyfin>
* 介紹:

![07](/attachments/2021-03-20-self-hosted-with-docker/07.png)

### kutt
可以用自己的域名，做短網址
* image: [kutt/kutt](https://hub.docker.com/r/kutt/kutt)
* github: <https://github.com/thedevs-network/kutt>
* 介紹:

![08](/attachments/2021-03-20-self-hosted-with-docker/08.png)

### mailpile
一個email的client，不錯用，但我也很少用
* image: 他沒有發布，但可以用`Dockerfile`自己build
* github: <https://github.com/mailpile/Mailpile>
* 介紹:

![09](/attachments/2021-03-20-self-hosted-with-docker/09.png)

### navidrome
用go寫的專門給音樂的媒體伺服器，基本上他的功能jellyfin也有，但比較專精在音樂，速度也比jellyfin快很多
* image: [deluan/navidrome](https://hub.docker.com/r/deluan/navidrome)
* github: <https://github.com/navidrome/navidrome>
* 介紹:

![10](/attachments/2021-03-20-self-hosted-with-docker/10.png)

### nps + npc
這真的超級方便的，一個反向代理工具，但是我不好解釋他在幹麻，可以看看別人和官網的介紹
* image: [ffdfgdfg/nps](https://hub.docker.com/r/ffdfgdfg/nps)
* github: <https://github.com/ehang-io/nps>
* 介紹:

![11](/attachments/2021-03-20-self-hosted-with-docker/11.png)

### openvpn
用docker架vpn會快很多，也比較安全～
* image: [kylemanna/openvpn](https://hub.docker.com/r/kylemanna/openvpn/)
* github: <https://github.com/kylemanna/docker-openvpn>
* 介紹:

### openvpn-monitor
搭配openpvn使用，可以監看說目前openvpn的連線情形
* image: [ruimarinho/openvpn-monitor](https://hub.docker.com/r/ruimarinho/openvpn-monitor)
* github: <https://github.com/ruimarinho/docker-openvpn-monitor>
* 介紹:

![12](/attachments/2021-03-20-self-hosted-with-docker/12.png)

### pgadmin
[postgresql](https://www.postgres.org)管理程式[pgadmin](https://www.pgadmin.org)的docker版
* image: [dpage/pgadmin4](https://hub.docker.com/r/dpage/pgadmin4)
* github:
* 介紹: 

![13](/attachments/2021-03-20-self-hosted-with-docker/13.png)

### photoprism
google再養套殺了，google photo不能無限上傳，教育版google也要縮水了，就該自架一個相片管理系統拉~，寫了這個才發現，我都拍一些拉基東西而已＝＝
* image: [photoprism/photoprism](https://hub.docker.com/r/photoprism/photoprism)
* github: <https://github.com/photoprism/photoprism>
* 介紹:

![14](/attachments/2021-03-20-self-hosted-with-docker/14.png)

### plik
算是自架免空拉，可以限制只有自己才能上傳，還能設密碼，分享檔案的時候很方便
* image: [rootgg/plik](https://hub.docker.com/r/rootgg/plik)
* github: <https://github.com/root-gg/plik>
* 介紹:

![15](/attachments/2021-03-20-self-hosted-with-docker/15.png)

### portainer
這應該蠻有名的，在網頁上管理docker的工具，我也不常用就是了
* image: [portainer/portainer-ce](https://hub.docker.com/r/portainer/portainer-ce)
* github: <https://github.com/portainer/portainer >
* 介紹:

![16](/attachments/2021-03-20-self-hosted-with-docker/16.png)
  
### qbittorrent
就是bt下載軟體拉，用他的webui界面載pt，再搭配jellyfin，就是看電影一條龍了
* image: [linuxserver/qbittorrent](https://hub.docker.com/r/linuxserver/qbittorrent)
* github: <https://github.com/linuxserver/docker-qbittorrent>
* 介紹:

![17](/attachments/2021-03-20-self-hosted-with-docker/17.png)

### resilio sync
也是很有名的p2p同步軟體，可以在手機或其他點腦上設定同步，把檔案備份回來
* image: [ghcr.io/linuxserver/resilio-sync](https://hub.docker.com/r/linuxserver/resilio-sync)
* github: <https://github.com/linuxserver/docker-resilio-sync>
* 介紹

![18](/attachments/2021-03-20-self-hosted-with-docker/18.png)

### trilium
一個作筆記的，有點像是evernote那種的取代，也有線上的web ui，不過功能好像更多，可以參考一下這個:[Trilium：超高自由度的个人知识库（基础篇）](https://sspai.com/post/59739)
* image: [zadam/trilium](https://hub.docker.com/r/zadam/trilium)
* github: <https://github.com/zadam/trilium>
* 介紹

![19](/attachments/2021-03-20-self-hosted-with-docker/19.png)

### wallabag
[pocket](https://getpocket.com/)的self-host拉，可以把網頁存起來之後看，而且他chrome擷取的外掛擷取的網頁，還蠻好看的
* image: [wallabag/wallabag](https://hub.docker.com/r/wallabag/wallabag)
* github: <https://github.com/wallabag/docker>
* 介紹:

![20](/attachments/2021-03-20-self-hosted-with-docker/20.png)


### webdav
就是那個webdav，輕鬆架設webdav伺服器，目前我是架給[zotero](https://www.zotero.org/)和[joplin](https://joplinapp.org/)用
* image: [bytemark/webdav](https://hub.docker.com/r/bytemark/webdav)
* github: <https://github.com/BytemarkHosting/docker-webdav>
* 介紹

### xmrig
挖門羅幣xmr的程式，xmrig的docker image，主要是蠻方便的，缺點是container的不支援顯示卡挖，我也不常挖，因為沒有設備qq，下圖是小湯匙加減挖><
* image: [metal3d/xmrig](https://hub.docker.com/r/metal3d/xmrig)
* github: <https://github.com/metal3d/docker-xmrig>
* 介紹

![21](/attachments/2021-03-20-self-hosted-with-docker/21.png)


### youtubedl-material
下載youtube音樂或影片很方便的工具，把它架起來之後，可以在網頁書籤上放個超連結，，遇到喜歡的就給他按下去，配合jellyfin又可以一條龍了，載完就出現在jellyfin媒體褲裡面了～～
* image: [tzahi12345/youtubedl-material](https://hub.docker.com/r/tzahi12345/youtubedl-material)
* github: <https://github.com/Tzahi12345/YoutubeDL-Material>
* 介紹: 

![22](/attachments/2021-03-20-self-hosted-with-docker/22.png)


## 架那麼多服務要幹麻，真的有在用？
其實就是一個字，爽，而已...，有些是真的常用，有些我也根本沒在用哈哈，但是現在有docker在，架個服務已經不用從環境配置安裝，解決一堆相依性問題之類的開始了，只要用docker + docker-compose，根本就是秒架，而且還能自己無限擴充，不用動不動用啥功能就付費版跳出來問你要不要，還蠻有成就感的，我也是今天寫這篇才發現，不知不覺我也搞那麼多出來了～～

目前的"介紹"都是空的，我會有空的時候把他寫出來，最終目標變成一個合集，大概都是週末的時候寫，也要看火什麼時候熄...，有可能突然就不更新了^^，其實照上面image進去的教學，自己用docker-compose都架的出來拉

之後的教學我都是用[docker-compose](https://docs.docker.com/compose/)，管理和除錯都很方便的工具！！







