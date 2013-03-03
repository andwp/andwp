---
layout: post
title: ScrollView 中嵌套ListView
category: Android开发
tags: null
---
{% include JB/setup %}
<p style="text-align: justify;">在android 的开发中，官方给出的建议是ScrollView中建议不要嵌套ListView，可是实际中可能会遇到一些迫不得已的情况，让我们需要实现这样的功能。  
ScrollView嵌套ListView往往会初现显示不全的问题，而且ScrollView可能会将ListView 的滑动事件覆盖了，两个控件的高度都是变动的，使得无法计算具体的高度。  
解决的思路是在设置完listAdapter过后，再根据ListView 的单个item重新设置ListAdapter的高度。</p>  
public static void reSetListViewHeight(ListView listView) {  
ListAdapter listAdapter = listView.getAdapter();  
if (listAdapter == null) {  
// pre-condition  
return;  
}  
  
int totalHeight = 0;  
for (int i = 0; i &lt; listAdapter.getCount(); i++) {  
View listItem = listAdapter.getView(i, null, listView);  
listItem.measure(0, 0);  
totalHeight += listItem.getMeasuredHeight();  
}  
  
ViewGroup.LayoutParams params = listView.getLayoutParams();  
params.height = totalHeight + (listView.getDividerHeight() * (listAdapter.getCount() - 1));  
listView.setLayoutParams(params);  
}  
<p style="text-align: justify;">参考来源 ：http://ryanjoy.iteye.com/blog/1291331</p>