---
layout: post
title: "NPS 反向代理，內網穿透工具，方便連上內網的網頁"
description: "NPS 反向代理，內網穿透工具，方便連上內網的網頁"
categories: [Docker,Linux]
---

NPS是一個方向代理工具，可以讓你很方便的連到內網，不用打開任何port，也不需要知道client的ip
<!--more-->

這篇會先介紹反向代理是啥，有什麼場景可以應用，server與client的安裝等，我還是習慣一切用docker，在部屬上會容易許多～

## 反向代理是啥
當我們想透過port連到電腦上的某個服務時(如ssh，vpn等)，一般情況下，電腦需要有公網ip，要連線的時候就能透過`ip:port`的方式連到電腦上，但是很多時候電腦會不能取得公網ip(接在分享器後，單位政策不讓你開port等)，這時候就需要反向代理工具拉

要實行反向代理，除了原本開port的電腦`client`，還需要有一台真的有公網ip的電腦`server`，透過NPS將`client`的port先轉送到`server`，我們就能先連到`server`上，NPS再幫我們連到`client`，實現反向代理，下面分別介紹利用docker在`server`與`client`的安裝，然後舉一些我有用到的場景與功能

## Server端安裝








