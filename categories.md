---
layout: page
title: 카테고리
permalink: /categories/
---

<div class="categories-page">
  {% for category in site.categories %}
    <h2 id="{{ category[0] | slugify }}">{{ category[0] }}</h2>
    <ul class="post-list">
      {% for post in category[1] %}
        <li class="post-item">
          <span class="post-date">{{ post.date | date: "%Y-%m-%d" }}</span>
          <h3>
            <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
          </h3>
          {% if post.tags.size > 0 %}
            <div class="post-tags">
              {% for tag in post.tags %}
                <a class="tag" href="{{ site.baseurl }}/tags/#{{ tag | slugify }}">{{ tag }}</a>
              {% endfor %}
            </div>
          {% endif %}
          <div class="post-excerpt">
            {{ post.excerpt | strip_html | truncatewords: 30 }}
          </div>
        </li>
      {% endfor %}
    </ul>
  {% endfor %}
</div>

<div class="category-index">
  <h2>카테고리 목록</h2>
  <ul>
    {% for category in site.categories %}
      <li><a href="#{{ category[0] | slugify }}">{{ category[0] }} ({{ category[1].size }})</a></li>
    {% endfor %}
  </ul>
</div>