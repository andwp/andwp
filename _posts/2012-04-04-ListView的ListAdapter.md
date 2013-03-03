---
layout: post
title: ListView的ListAdapter
category: Android开发
tags: null
---
{% include JB/setup %}
这里不是讨论<a title="ListView" href="http://developer.android.com/reference/android/widget/ListView.html" target="_blank">ListView </a>的用法，是在实际使用过程中对ListView中的配置参数ListAdapter的一些思考。  
大家知道android官网上的一个ListView的用法使用的是<a title="ListAdapter" href="http://developer.android.com/reference/android/widget/ListAdapter.html" target="_blank">SimpleAdapter</a> ，这个类其实是继承于<a href="http://developer.android.com/reference/android/widget/BaseAdapter.html" target="_blank">BaseAdapter</a> 这个抽象类的，BaseAdapter是实现了<a href="http://developer.android.com/reference/android/widget/ListAdapter.html" target="_blank">ListAdapter</a>的接口。  
  
在用的时候，我总觉得SimpleAdapter用着不是很爽。最后都用自定义的BaseAdapter来做参数。以前想的是实现都在内部，外面只传个数据，然后传个Context就可以了，根本不用管里面的实现。但是现在发现这样的结果是在使用的时候，每次都要去重写BaseAdapter来适应不同的需求。  使用起来十分不方便。  
  
干脆给实现BaseAdapter的类写一个构造函数，不用传Context，只传入一个外面配置好的List&lt;LinearLayout&gt;  ，这样的Adapter就可以通用了。以后只需要改写LienarLayout的生成类，就可以了。