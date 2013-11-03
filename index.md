---
layout: page
title: andwp's cook
tagline: Enjoy_Your_Time
---
{% include JB/setup %}  
#最近文章  
*************************************
<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
  
*************************************  
###friend link
<p>
<a href="http://zhenglyu.com" style="margin-right:80px">lyu</a>   
<a href="http://yomuse.de">悠木</a>  
</p>

