---
layout: page
title: Tags
---

{% assign tags = site.tags | sort %}

<div class="tag-list">
{% for tag in tags %}
  <h2 id="{{ tag[0] }}">
    <i class="fas {% case tag[0] %}
      {% when 'java' %}fa-java
      {% when 'python' %}fa-python
      {% when 'rust' %}fa-rust
      {% when 'mathematics' %}fa-square-root-variable
      {% when 'janestreet' %}fa-puzzle-piece
      {% else %}fa-tag
      {% endcase %}"></i>
    {{ tag[0] }}
  </h2>
  <ul>
    {% for post in tag[1] %}
      <li>
        <a href="{{ post.url }}">{{ post.title }}</a>
        <span class="post-date">{{ post.date | date: "%B %d, %Y" }}</span>
      </li>
    {% endfor %}
  </ul>
{% endfor %}
</div>