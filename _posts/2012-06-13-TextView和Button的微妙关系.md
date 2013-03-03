---
layout: post
title: TextView和Button的微妙关系
category: Android开发
tags: null
---
{% include JB/setup %}
public class Button extends TextView {  
public Button(Context context) {  
this(context, null);  
}  
  
public Button(Context context, AttributeSet attrs) {  
this(context, attrs, com.android.internal.R.attr.buttonStyle);  
}  
  
public Button(Context context, AttributeSet attrs, int defStyle) {  
super(context, attrs, defStyle);  
}  
}  
  
真的是一个东东哦，只是显示的style不一样com.android.internal.R.attr.buttonStyle  
刚刚才注意到sdk源码上的这段。。