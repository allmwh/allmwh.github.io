---
layout: post
title: "linux發送wake on lan 封包給其他電腦"
description: "linux發送wake on lan 封包給其他電腦"
categories: [Linux]
---

筆記一下使用Linux系統(CentOS、Ubuntu)透過shell發送wol封包給其他電腦

<!--more-->

## Ubuntu
### 安裝套件
在ubuntu中，套件名稱為`etherwake`，用apt安裝
```
apt install etherwake
```
### 發送wol封包
```
etherwake -i eth0  fc:bb:15:de:b4:ff
```
`eth0`為本機的網卡名，可用`ifconfig -a`查詢，指定wol封包透過哪個網卡送到網路上，再填入要開機電腦的MAC即可

## CentOS
### 安裝套件
CentOS的套件則為`net-tools`，用yum安裝
```
yum install net-tools
```

### 發送wol封包
```
ether-wake -i eth0  fc:bb:15:de:b4:ff
```
和Ubuntu中的指令差了一個`-`，Ubuntu沒有`-`，為`etherwake`

## 參考資料
* [CentOS How-Tos](https://www.centoshowtos.org/network-and-security/ether-wake/)
* [CentOS forums](https://forums.centos.org/viewtopic.php?t=59133)

