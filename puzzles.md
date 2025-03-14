---
layout: page
title: JaneStreet Puzzles
---

# JaneStreet Puzzle Archive

This is an archive of my attempts at solving [Jane Street's monthly puzzles](https://www.janestreet.com/puzzles/). Each entry includes the puzzle name, completion status, and my solution approach.

{% assign puzzle_posts = site.posts | where: "tags", "janestreet" %}
{% assign puzzle_posts = puzzle_posts | sort: "date" | reverse %}

<ul class="puzzle-archive">
{% for post in puzzle_posts %}
  <li>
    <span class="puzzle-date">{{ post.date | date: "%B %Y" }}</span>
    <a href="{{ post.url }}">{{ post.title }}</a>
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