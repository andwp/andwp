---
layout: post
title: SilverLight中的数据绑定
category: silverlight开发
tags: null
---
{% include JB/setup %}
由于一个很低级的错误，让我调试了好久。  
从数据库中取出DataTable，然后转换成我定义的结构List&lt;Person&gt; ，用来和DataGrid.ItemSource绑定。。前端代码已经为每一列添加了数据源 bing。可是不管怎么都不显示数据。后来发现定义的结构person写成了内部类，并且申明为private。，应该是在绑定发生的时候，代码访问不了此类。  
  
最后声明成public 就ok了。基础不好害死人