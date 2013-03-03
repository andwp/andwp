---
layout: post
title: android gps打开状态
category: Android开发
tags: null
---
{% include JB/setup %}
很多应用需精确定位，如果此时用户没有打开gps，就无法获得精确的经纬度。  
判断gps是否打开，其实就一句话。  
     		  
// 获取GPS现在的状态   
 boolean gpsEnabled = Settings.Secure.isLocationProviderEnabled(  
		getContentResolver(), LocationManager.GPS_PROVIDER);   
那如果没有打开，需要打开gps呢？开始搜到一·篇很老的帖，说到用  
     Settings.Secure.setLocationProviderEnabled( getContentResolver(), LocationManager.GPS_PROVIDER, false );   
的方法可以直接打开/关闭gps。  
结果是很显示行不通的，如果可以直接关闭或打开，那么多的应用干嘛要让用户手动设置。原来在android sdk 1.0上，是可以直接通过代码设置的，后来也许是出于安全的考虑，这种方式在后来的sdk中行不通了。  
那么还是只有让用户手动设置了。  
     	  
Intent intent =   
    new Intent(android.provider.Settings.ACTION_LOCATION_SOURCE_SETTINGS);				intent.addCategory(Intent.CATEGORY_DEFAULT);  
startActivity(intent);  
 