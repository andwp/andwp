---
layout: post
title: android Notification设置不可清除
category: Android开发
tags: [通知栏 , 移除 ]
---
{% include JB/setup %}
     private void notificationShow() {  
  
// 定义通知栏展现的内容信息  
int icon = R.drawable.ic_launcher;  
CharSequence tickerText = "运动追踪";  
long when = System.currentTimeMillis();  
Notification notification = new Notification(icon, tickerText, when);  
  
// 定义下拉通知栏时要展现的内容信息  
Context context = getApplicationContext();  
CharSequence contentTitle = "运动追踪";  
CharSequence contentText = "正在运行 Running";  
Intent notificationIntent = new Intent(this, MainActivity.class);  
PendingIntent contentIntent = PendingIntent.getActivity(this, 0,  
notificationIntent, 0);  
notification.setLatestEventInfo(context, contentTitle, contentText,  
contentIntent);  
// 设置不可清除  
notification.flags = Notification.FLAG_NO_CLEAR;  
mNotificationManager.notify(NOTIFICATIONID, notification);  
} 