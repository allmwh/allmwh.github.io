---
layout: post
title: "ubuntu 音訊訊號持續輸出，解決耳機播放雜音"
description: "ubuntu 音訊訊號持續輸出，解決耳機播放雜音"
categories: [linux]
---

Ubuntu會在**沒有播放聲音的時候，停止輸出音訊訊號**，這樣會有一些問題，比如說聲音的一開始都會沒聽到，或是耳機常常有因為聲音訊號開啟或關閉的雜音，找了老半天資料，終於有解法
<!--more-->

## 將module-suspend-on-idle註解掉
解法很簡單，只要去`/etc/pulse/default.pa`註解掉一行
```
sudo vim /etc/pulse/default.pa
```

將`load-module module-suspend-on-idle`註解掉，wq存檔
```
### Automatically suspend sinks/sources that become idle for too long
# load-module module-suspend-on-idle
```

音訊服務重開，或是直接重開機，就不會有擾人的噪音了
```
pulseaudio -k
```

最近把筆電灌成Ubuntu 20.04，發現現在的Ubuntu比以前好用多了，驅動全部都幫你裝好，包含nvidia顯卡，也不會有亮度無法調整的問題，很多gnome exension都可以個性化，界面也蠻好看的，不過還是很多東西要調校，但感覺可以取代掉windows做桌面系統了，之後再慢慢把有條校的東西放上來
## 參考資料
* [Keep audio “awake”](https://askubuntu.com/questions/1015384/keep-audio-awake)