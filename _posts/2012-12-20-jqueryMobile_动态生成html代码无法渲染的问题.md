---
layout: post
title: jqueryMobile 动态生成html代码无法渲染的问题
category: Android开发
tags: [android , phonegap , jqm ]
---
{% include JB/setup %}
 无论是通过js初始化页面，还是在ajax请求后返回结果更新ui。只要是通过js直接生成的html元素，是没有渲染过的。这个时候不管是ui效果还是其它资源引用，都是无法实现的。  
看到有人说在执行玩js代码后条用.page()方法可以解决该问题：$('#containerpageid').page();  
试了下，没有成功，后来通过$('#viewContent').trigger("create");方法成功渲染对象。  
ps：这几天在用phonegap+jqueryMobile做些小应用。其开发速度毋庸置疑。至于效率嘛。。那就真比原生应用差得太多太多了。。。  
如果在这点上能有所提高，那么html5的春天才是真正来了。  
