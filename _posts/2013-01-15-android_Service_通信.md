---
layout: post
title: android Service 通信
category: Android开发
tags: null
---
{% include JB/setup %}
总结一下Service 和Activity 的通信：  
1. 主要分成两种情况，即进程间通信和进程内通信  
2. 进程内通信简单点，主要需要复写onBind 方法 ，在Activity中使用bindService即可；  
3. 进程间通信有两种：  
 1）用AIDL（Android Interface Definition Language）实现，实现相对复杂，需要了解AIDL的相关知识，Activity中使用bindService启动服务；  
 2）用Messenger实现，实现相对简单，（底层也是用的AIDL，不过所有Activty传来的消息都会排入队列中处理）是线程安全的；   
  
这里有点疑问：  
bindService启动的服务都是随着启动的Context的关闭而关闭，也就是说需要依赖于启动该Service的Activity， 而只有用这种方式，才能进行Activity和Service的通信。那如果一个Service 是通过startService()来启动的， 有什么好的方法与Service通信呢？   
  目前能想到的就是广播机制，但不知道是不是最好的方法。