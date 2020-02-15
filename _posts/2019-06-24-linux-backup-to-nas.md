---
layout: post
title: 備份linux上的資料到synology nas (不需使用rsync+crontab)
description: 使用synology的套件 active backup for business 可以直接使用ssh對於linux系統作定時備份
categories: [資訊,Linux]
---
之前寫過一篇linux rsync+crontab實現定時備份是把每台電腦都設rsync備份到nas上，但是這方法需要到每台電腦上都設定腳本檔，最近發現**synology 的NAS有一個超方便的工具，可以直接在NAS上操作所有的動作**，不用跑到每台電腦上設定

只要linux電腦有預設安裝SSH和rsync就可以用了!

<!--more-->

先在synology上安裝**active backup for business**

![圖片_005](/attachments/2019-06-24-linux-backup-to-nas/圖片_005.png)

安裝後打開選 檔案伺服器>>新增伺服器>>選rsync伺服器

![圖片_007-1](/attachments/2019-06-24-linux-backup-to-nas/圖片_007-1.png)

rsync伺服器我自己的例子是基本上linux都會內建，SSH也是，所以不需要特別安裝

將自己的port、**LINUX使用者帳密填上去**，若要在外網連線的話，需要把ssh的port通過分享器的防火牆，使用者的話我為了方便，直接用root(雖然危險一點點，不過我都在內網)，要直接用root記得去ssh設定允許root登入

![圖片_009-1](/attachments/2019-06-24-linux-backup-to-nas/圖片_009-1.png)

設定成功後，就可以來設定備份方式了，有三種方式可以選，依自己需求

![圖片_010-1](/attachments/2019-06-24-linux-backup-to-nas/圖片_010-1.png)

選備份的資料夾，之後就是一些排程的設定，備份資料夾，還有版本保留的方式，都很簡單~~

![圖片_012](/attachments/2019-06-24-linux-backup-to-nas/圖片_012.png)

在任務清單中，就可以看到剛剛加的任務

![圖片_013](/attachments/2019-06-24-linux-backup-to-nas/圖片_013-1581477149031.png)

**總覽**中也可以看到每天的備份狀態，跟之前用rsync比起來方便很多

![圖片_014](/attachments/2019-06-24-linux-backup-to-nas/圖片_014.png)



需要還原只要打開**active backup for business portal**，選特定檔案還原就直接幫你把檔案放回伺服器

雖然有點打之前自己的臉，不過誰不想要方便懶惰一點呢~~~