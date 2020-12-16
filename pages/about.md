---
layout: post
title: 關於我
permalink: /about/
---

紀錄在生活上學到的東西

### 履歷
WIP

### 學經歷

* 國立陽明大學，生化所 / Jul 2020 - Present
  
* 北海道大學，農學部交換 / Mar 2018 - Aug 2018
 <br><img src="/attachments/about/hokudai.jpg" alt="hokudai" class="about-img" />
* 國立臺灣海洋大學，生科系 / Sep 2016 - Jun 2020
 <br><img src="/attachments/about/ntou.jpg" alt="ntou" class="about-img" />
### 技能

<!-- ### 技能樹 -->

<!-- <div>
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
</div> -->

### 連繫

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

### Jekyll 佈景主題

網站使用Zohar大大的theme，再自行加上慣用的評論，分享系統，繁體中文化

Theme repo:<https://github.com/zoharyips/zoharyips.github.io>



