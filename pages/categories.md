---
layout: page
title: 按類別排列
description: 文章產能不足......
comments: false
share: false
repositories: false
categories: true
canvas: true
menu: 分類
permalink: /categories/
---

<div>
  {% assign sorted_categories = site.categories | sort %}
  {% for category in sorted_categories %}
    <h3>{{ category | first }}</h3>
    <ol class="posts-list" id="{{ category[0] }}">
      {% for post in category.last %}
        <li class="posts-list-item">
          <span class="posts-list-meta">{{ post.date | date:"%Y-%m-%d" }}</span>
          <a class="posts-list-name" href="{{ site.url }}{{ post.url }}">{{ post.title }}</a>
        </li>
      {% endfor %}
    </ol>
  {% endfor %}
</div>