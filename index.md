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

####写在前面

以前辗转过两个网易博客，有一个还残余一些日志，有些日志从第一个那里迁移得不完全还有些残缺([我的网易博客](http://cheesefan.blog.163.com/))。Github上也是搭了又删，删了又搭，最后还是搞个简易点的吧，用Jekyll Bootstrap默认主题稍微有个布局。以后还是把重点放在内容上吧，记录一些一个学生菜鸟的学习备忘。

Email:  fcx600@163.com
    
Github: [Corey600 (Corey Fei)](https://github.com/Corey600)
