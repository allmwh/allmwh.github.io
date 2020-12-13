---
layout: post
title: "快速建立類似於VPN的虛擬網路，不用在server端安裝-sshuttle"
description: "快速建立類似於VPN的虛擬網路，不用在server端安裝-sshuttle"
categories: [Linux]
---

sshuttle可以幫助快速建立與遠端電腦的網路通道，不需在server特別安裝東西，只需要在server有`ssh`與`python`就可以連結server端的子網
<!--more-->

## repo
> <https://github.com/sshuttle/sshuttle>
> 
> <https://sshuttle.readthedocs.io/en/stable/index.html>


## 安裝sshuttle in client

sshuttle已經包含在很多linux的發行版的包當中，直接使用軟體管理工具安裝就可了，以ubuntu為例:
```bash
sudo apt-get install sshuttle
```
其他的發行版就參考他的repo吧

## 連線
很像ssh連接的方式，打上帳號密碼，還有哪些流量要轉發到遠端
```bash
sshuttle -r username@sshserver:port 0.0.0.0/0
```
### 代理特定子網
也可指定只代理server端的特定子網
```bash
 sshuttle -r username@remotehost:port 10.0.0.0/8
```
### 使用ssh private key連接
若server端是採用金鑰登入，那sshuttle也要用那個key，記得key的權限要是`600`，不然ssh會報錯哦
```bash
chmod 600 /your/key/path
sshuttle -r username@remotehost:port 0/0 --ssh-cmd 'ssh -i /your/key/path'
```

真的蠻方便的，有臨時情況想用server端的內網或ip的話，就不用特地架個vpn出來

## 參考資料
* [sshuttle: where transparent proxy meets VPN meets ssh](https://github.com/sshuttle/sshuttle)
* [How to use sshuttle with .key, .csr or .pem files for authentication](https://gist.github.com/Davor111/4b6a3d638b5e7abdb8910f87d20e40d2)
* [使用 sshuttle 构建一个穷人的虚拟专网](https://zhuanlan.zhihu.com/p/87427476)