---
# You don't need to edit this file, it's empty on purpose.
# Edit theme's home layout instead if you wanna make some changes
# See: https://jekyllrb.com/docs/themes/#overriding-theme-defaults
#layout: home
layout: page
title: Home
tagline: Here's posts list.
---

<ul class="posts">
  {% for post in site.posts %}
    <li>
      <span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a>
      <article class="excerpt">{{post.excerpt}}</article>
      <a class="pull-right marginBottom10" href="{{post.url | prepend: site.baseurl }}">Read More</a>
    </li>
  {% endfor %}
</ul>

--------------------

Email: fcx600@163.com       
Github: [Corey600 (Corey Fei)](https://github.com/Corey600)
