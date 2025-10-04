---
layout: page
title: "Categories"
permalink: /category
---

{% assign cats = site.posts | map: 'categories' | join: ',' | split: ',' | uniq | sort %}
{% for cat in cats %}
  {% if cat != '' %}
  <h2 id="{{ cat | slugize }}">{{ cat }}</h2>
  <ul>
    {% for post in site.posts %}
      {% if post.categories contains cat %}
      <li>
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
        <span class="post-date"> — {{ post.date | date: site.plainwhite.date_format }}</span>
      </li>
      {% endif %}
    {% endfor %}
  </ul>
  {% endif %}
{% endfor %}
