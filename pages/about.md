---
layout: post
title: 關於我
permalink: /about/
---

allmwh，熱愛資訊的一切東西，原本想要讀資工，原本打算全身踏進碼農世界，但最終跑來了...生科==，目前生科系大四，順理成章的要讀研究所了，期望能找到生科與資訊的結合，成為有＂生物資訊＂專長的人，想多了解機器學習、系統架構、還想再加點前端

### CV正式版

WIP

### CV唬爛版

- 面試不會加分的棒子
- 可撥生科系QQ，所以很窮
- 對資訊有興趣，但不知為啥跑來生科，所以懂得很皮毛
- ==中間不空格的使用者
- 乃木坂粉
- 二乃我婆>< (2020/01/15更新)

### 聯繫方式

<div>
  <ul style="line-height: 3rem;list-style-type: none;">
    {% for obj in site.data.social %}
    <li>
      <img width="32" height="32" style="margin-right:0.375rem;vertical-align: middle;" src="{{ obj.svg }}"/>&nbsp;
      <a href="{{ obj.url }}" title="{{ obj.title }}" style="white-space:pre"><code>{{ obj.sitename }}</code> {{ obj.name }}</a>
    </li>
    {% endfor %}
  </ul>
</div>

### 技能樹

<div>
<ul style="list-style-type: none;">
    {% for skill in site.data.skills %}
      <li>
        <h4>{{ skill.name }}</h4>
        <div class="btn-inline">
          {% for keyword in skill.keywords %}
            <button class="btn btn-outline" type="button">{{ keyword }}</button>
          {% endfor %}
        </div>
      </li>
    {% endfor %}
 </ul>
</div>

### Jekyll 佈景主題

網站使用[Zohar](https://zoharyip.club/)大大的theme，再自行加上慣用的評論，分享系統，繁體中文化

Theme repo:[https://github.com/zoharyips/zoharyips.github.io](https://github.com/zoharyips/zoharyips.github.io)

### 大事記

#### 2020/02/09

wordpress實在太慢了qqq，所以踏進了靜態網頁的世界，明明前端甚麼的都還是不懂，之後再慢慢把wp搬過來，邊摸邊學吧~~

------

#### 2019/12/14

最近真的窮到靠北，所以加了一like bottom，文章對您有幫助的話，拜託幫我按個讚拉，我也會努力產文的

------

#### 2019/11/23

推甄推完了… 意外的成果不錯
之後再來分享推甄心得

------

#### 2019/04/16

還是忍不住，從免費空間搬到電腦上了><

產出文章量=0

seo優化也好難做 暫時先這樣掛著吧

------

#### 2019/03/16

之前在medium創blog，種種原因沒寫又肚爛(原因大概和日本那時一樣==)，之後搬來這裡

目標:把wordpress的免費空間寫爆，付錢，不然每次都不能堅持

然後這次狠下心來還是另有原因的，一年後看有沒有效再說出來吧



