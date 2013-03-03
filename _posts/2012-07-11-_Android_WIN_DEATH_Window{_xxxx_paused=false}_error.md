---
layout: post
title:  Android WIN DEATH Window{ xxxx paused=false} error
category: Android开发
tags: null
---
{% include JB/setup %}
得到个WIN DEATH: Window{ xxxx paused=false} error?  
是在一个登陆界面后就输出这个信息，调试的时候跳过此界面就直接终止调试了。  
花了一个上午都没有找到原因，百思不得其解啊。  
就在我要崩溃的时候，在登录界面的代码里发现一个finish()的重载  
  
       
@Override  
public void finish() {  
super.finish();  
System.exit(0);  
}  
   
--------------------------------------------------  
深感惭愧。。。直接在这里退出了，activity还在，但是程序已经退出了。。