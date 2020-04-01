---
layout: post
title: 解決wordpress 5.2不能更新-centos7 linux權限調整
description: 因為LINUX的檔案權限及SELINUX設定不對導致wordpress無法更新的問題
categories: [Linux,Wordpress]

---

剛在更新wordpress時，跑出了這個 ， 想想大概就是權限的問題

> 由於複製檔案失敗，所以無法安裝更新。這通常是由不正確的檔案權限所致

<!--more-->

## 先確認資料夾權限

使用 ls -l 到網頁資料確認使用者，資料夾的擁有者須為網頁伺服器的使用者(如centos的apache的使用者為"apache")

```bash
# ls -l /var/www/html/wordpress

-rwxr-xr-x.  1 apache apache   420 12月  1  2017 index.php
-rwxr-xr-x.  1 apache apache 19935  5月 15 00:40 license.txt
-rwxr-xr-x.  1 apache apache  7300  5月 15 00:40 readme.html
...
```

若使用者為root或其他的，就會沒有權限，透過chown更改權限 ， 這樣大概就可以成功更新了!

```bash
# chown -R apache:apache /var/www
```

## 還不行的話，關掉SELinux

SELinux簡單來說就是讓linux很安全吧，所以很多權限都會被限制，我自己更新失敗也是關掉SELinux後才成功的

查看SELinux狀態 ， Current mode為**enforcing**的時候，SELinux是打開的

```bash
# sudo sestatus

SELinux status:                 enabled
SELinuxfs mount:                /sys/fs/selinux
SELinux root directory:         /etc/selinux
Loaded policy name:             targeted
Current mode:                   enforcing
Mode from config file:          error (Success)
Policy MLS status:              enabled
Policy deny_unknown status:     allowed
Max kernel policy version:      31
```

輸入setenforce 0將SELinux暫時關閉

```bash
# setenforce 0
# sestatus

SELinux status:                 enabled
SELinuxfs mount:                /sys/fs/selinux
SELinux root directory:         /etc/selinux
Loaded policy name:             targeted
Current mode:                   permissive
Mode from config file:          error (Success)
Policy MLS status:              enabled
Policy deny_unknown status:     allowed
Max kernel policy version:      31
```

執行**setenforce 0**後，Current mode就會變成permissive，代表SELinux已被暫時關閉了，這時再回到wordpress後台就能正常更新了

上述更改SELinux的設定只是暫時的，重開機後就會恢復原本的設定，若要永久修改，可以編輯一下設定檔， 更改SELinux為關閉>>**SELINUX=disable**，這樣就會永久保留設定囉

```bash
# vim /etc/selinux/config

# This file controls the state of SELinux on the system.
# SELINUX= can take one of these three values:
#     enforcing - SELinux security policy is enforced.
#     permissive - SELinux prints warnings instead of enforcing.
#     disabled - No SELinux policy is loaded.
SELINUX=disable
# SELINUXTYPE= can take one of three values:
#     targeted - Targeted processes are protected,
#     minimum - Modification of targeted policy. Only selected processes are protected. 
#     mls - Multi Level Security protection.
SELINUXTYPE=targeted
```


## 參考資料

[CentOS 7 開啟/關閉SELinux](https://www.brilliantcode.net/145/centos-7-check-selinux-status-enabled-or-not/)