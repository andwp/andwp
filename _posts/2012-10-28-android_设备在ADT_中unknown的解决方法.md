---
layout: post
title: android 设备在ADT 中unknown的解决方法
category: Android开发
tags: null
---
{% include JB/setup %}
前提是本机（linux）已经能够识别android设备。只是偶尔抽风，导致无法识别设备的情况。  
直接下面代码保存成脚本android_reset_devices.sh   
       
adb kill-server  
sudo service udev stop  
adb start-server  
adb devices  
sudo service udev start  
   
加权限   
#chmod u+x android_reset_devices.sh   
执行  
#./android_reset_devices.sh  
以后出问题直接运行该脚本即可！  
