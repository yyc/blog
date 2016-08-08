---
layout: default
title: Welcome!
tagline: Supporting tagline
---
{% include JB/setup %}

  {% for post in site.posts %}
  <div class='post'>
    <h2><a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></h2>
    <span>{{ post.date | date_to_string }}</span>
    <hr />
    {{ post.content }}
  </div>
  {% endfor %}
