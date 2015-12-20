---
layout: page
title: Home
tagline: Here's posts list.
---
{% include JB/setup %}

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

--------------------

Email: fcx600@163.com       
Github: [Corey600 (Corey Fei)](https://github.com/Corey600)