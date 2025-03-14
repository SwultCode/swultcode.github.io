---
layout: page
title: JaneStreet Puzzles
---

<link href="/css/override.css" rel="stylesheet" type="text/css">
<link href="/css/tags.css" rel="stylesheet" type="text/css">
<link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">

{% include tag.html %}

# JaneStreet Puzzle Archive

This is an archive of my attempts at solving [Jane Street's monthly puzzles](https://www.janestreet.com/puzzles/). Each entry includes the puzzle name, completion status, and my solution approach.

{% assign puzzle_posts = site.posts | where: "tags", "janestreet" %}
{% assign puzzle_posts = puzzle_posts | sort: "date" | reverse %}

<ul class="puzzle-archive">
{% for post in puzzle_posts %}
  <li>
    <span class="puzzle-date">{{ post.date | date: "%B %Y" }}</span>
    <a href="{{ post.url }}">{{ post.title }}</a>
    {% assign filtered_tags = "" | split: "" %}
    {% for tag in post.tags %}
      {% if tag != "janestreet" %}
        {% assign filtered_tags = filtered_tags | push: tag %}
      {% endif %}
    {% endfor %}
    {% include tag.html tags=filtered_tags %}
    
    {% if post.completed %}
    <span class="puzzle-status completed">Completed</span>
    {% else %}
    <span class="puzzle-status attempted">Attempted</span>
    {% endif %}
  </li>
{% endfor %}
</ul>

{% if puzzle_posts.size == 0 %}
<p>No puzzle solutions posted yet. Check back soon!</p>
{% endif %}