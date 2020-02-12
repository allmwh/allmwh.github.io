---
layout: post
title: 將lm-sensors的CPU溫度資料回報到datadog上
description: 將lm-sensors的CPU溫度資料回報到datadog上
categories: [資訊,Linux,MyRepo]
---
[datadog](https://www.datadoghq.com/)是個很好的資料收集平台，一個使用的例子是拿來監控電腦，效能、溫度…，不過datadog的agent沒有內建監測溫度的功能，所以**我就寫了一個外掛監測，並回報資料**

<!--more-->

## 演示

我把相關教學放在我的github上了: [https://github.com/allmwh/datadog-sensors]( https://github.com/allmwh/datadog-sensors)
這邊只做一些演示

![demo](/attachments/2019-07-20-lm-sensors-in-datadog/demo.png)

很多台電腦同時安裝後，可以做一個監控頁面，所有電腦的狀態都很清楚
datadog功能很多，還可以設定到一定溫度就寄email的功能

![圖片_015](/attachments/2019-07-20-lm-sensors-in-datadog/圖片_015.png)

## 監測nvidia顯卡以及apc ups

我也依照這個概念寫了監測nvidia顯卡和apc ups的工具，需要的可以去看看

datadog-nvidiasmi: [https://github.com/allmwh/datadog-nvidiasmi]( https://github.com/allmwh/datadog-nvidiasmi)

datadog-apcaccess:[https://github.com/allmwh/datadog-apcaccess](https://github.com/allmwh/datadog-apcaccess)