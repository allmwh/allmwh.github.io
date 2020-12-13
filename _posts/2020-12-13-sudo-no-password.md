---
layout: post
title: "sudo指令不用打密碼"
description: "sudo指令不用打密碼"
categories: [Linux]
---

稍微紀錄一下怎麼讓sudo的時候不用打密碼
<!--more-->

使用以下指令去更改`/etc/sudoers`
```bash
sudo visudo
```

將`%sudo   ALL=(ALL:ALL) ALL`改成
```bash
%sudo   ALL=(ALL:ALL) NOPASSWD:ALL
```
存檔離開後就可以了，這樣以後就不用一直打密碼，不過有安全上的問題，使用的時候請小心哦

