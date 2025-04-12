---
layout: page
title: 태그
permalink: /tags/
---

<div class="tags-page">
  <div class="tag-cloud">
    <h2>태그 클라우드</h2>
    {% assign tags = site.tags | sort %}
    {% for tag in tags %}
      <a class="tag" href="#{{ tag[0] | slugify }}" 
         style="font-size: {{ tag[1].size | times: 4 | plus: 80 }}%">
        {{ tag[0] }} <span>({{ tag[1].size }})</span>
      </a>
    {% endfor %}
  </div>

  <div class="tag-list">
    {% for tag in tags %}
      <h2 id="{{ tag[0] | slugify }}">{{ tag[0] }}</h2>
      <ul class="post-list">
        {% for post in tag[1] %}
          <li class="post-item">
            <span class="post-date">{{ post.date | date: "%Y-%m-%d" }}</span>
            <h3>
              <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
            </h3>
            {% if post.categories.size > 0 %}
              <div class="post-categories">
                카테고리:
                {% for category in post.categories %}
                  <a href="{{ site.baseurl }}/categories/#{{ category | slugify }}">{{ category }}</a>{% unless forloop.last %}, {% endunless %}
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
</div>