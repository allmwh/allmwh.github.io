---
layout: post
title: "Ubuntu 20.04 安裝vnc server"
description: "Ubuntu 20.04 安裝vnc server"
categories: [Linux]
---

紀錄一下安裝vnc-server with xfce，開成服務，剪貼簿功能
<!--more-->

## 安裝所需套件

tigervnc server
```bash
sudo apt install tigervnc-standalone-server tigervnc-common autocutsel
```

桌面環境，gnome打不開，用xfce
```bash
sudo apt install xfce4 xfce4-goodies
```

## 設定vnc
### 密碼
輸入`vncpasswd`設定登入密碼
### 啟動環境
`vim ~/.vnc/xstartup`
```bash
#!/bin/bash

export SHELL=/bin/bash

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
vncconfig -nowin &
autocutsel -fork
startxfce4 &

```
讓`~/.vnc/xstartup`可以執行`chmod +x ~/.vnc/xstartup`

這時候就可以用vncserver開了，不過我們可以把他用成服務
## 設成服務
`sudo vim /etc/systemd/system/vncserver@.service`，裡面可以條解析度，`username`記得都換掉
```bash
[Unit]
Description=Start TightVNC server at startup
After=syslog.target network.target

[Service]
Type=forking
User=sammy
Group=sammy
WorkingDirectory=/home/sammy

PIDFile=/home/sammy/.vnc/%H:%i.pid
ExecStartPre=-/usr/bin/vncserver -kill :%i > /dev/null 2>&1
ExecStart=/usr/bin/vncserver -depth 24 -geometry 1280x800 -localhost :%i
ExecStop=/usr/bin/vncserver -kill :%i

[Install]
WantedBy=multi-user.target
```
* 重整服務`sudo systemctl daemon-reload`
* 啟用`sudo systemctl enable vncserver@1.service`
* 開啟`sudo systemctl start vncserver@1`
* 停止`sudo systemctl stop vncserver@1`

如果服務怪怪的，可以直接殺`vncserver -kill :1`

這樣就裝完拉，搭配[guacamole](https://guacamole.apache.org/)起來超級方便的，這個也一定要寫起來的，改天吧

![01](/attachments/2021-03-07-vncserver/01.png)

## 參考資料
* [Ubuntu 20.04 Remote Desktop Access with VNC](https://www.answertopia.com/ubuntu/ubuntu-remote-desktop-access-with-vnc/)
* [ How to Install and Configure VNC on Ubuntu 20.04 [Quickstart]](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-20-04-quickstart)
* [Clipboard does not work using tigervnc, even with options enabled on client and server](https://superuser.com/questions/1521267/clipboard-does-not-work-using-tigervnc-even-with-options-enabled-on-client-and)