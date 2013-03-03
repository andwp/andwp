---
layout: post
title: android中不同屏幕的UI 
category: Android开发
tags: null
---
{% include JB/setup %}
<a href="http://developer.android.com/training/multiscreen/screendensities.html">官方描述：</a>  
<blockquote>To generate these images, you should start with your raw resource in vector format and generate the images for each density using the following size scale:  
<ul>  
	<li>     xhdpi : 2.0</li>  
	<li>     hdpi : 1.5</li>  
	<li>     mdpi : 1.0 (baseline)</li>  
	<li>     ldpi : 0.75</li>  
</ul>  
</blockquote>  
所以，一般的比例应该是3：4：6：8，做UI 必须注意这点。mark 到这里