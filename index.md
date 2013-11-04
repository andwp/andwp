---
layout: page
title: andwp's cook
tagline: Enjoy_Your_Time
---
{% include JB/setup %}  
>最近文章
*************************************
<ul class="posts">
  {% for post in site.posts offset:0 limit:3 %}
    <li><span>{{ post.date | date:"%Y-%m-%d" }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
*************************************  
>友情链接
<a href="http://zhenglyu.com" style="margin-right:80px">lyu</a>   
<a href="http://yomuse.de">悠木</a>  


