---
layout: post
title: 实现android ListView的分组标签（思路）
category: Android开发
tags: null
---
{% include JB/setup %}
有两种思路，一种是做成一个ListView，然后在自定义的Adapter里面设置哪些项响应点击事件，哪些项不响应点击事件（重写BaseAdapter的 <span style="color: #008000;">  
</span>  
 public boolean isEnabled(int position) 方法 ）；另一个思路是设置成多个ListView,在显示标签的地方插入一项带TextView的Layout，然后把它们通过linearlayout布局到scrollview里面去。  
  
由于后者涉及到scrollview和listview的共存和事件监听不好控制，所以在正常情况下应该选择第一种思路。（但是我事先并没有想到第一种思路，所以有两个程序里的代码都用了后者--！）,一段时间过后，我使用的其中一个程序数据量开始变大起来。取数据的代码，都是放在另一个线程（非主线程）。而更新UI界面上的操作是放在UI主线程。由于数据量比较大，界面常常会被阻塞。  
然后我还是改用了第一种方法，只有一个listView 效率要高很多！！吸取教训，现在才意识到效率在手机开发的重要性。。