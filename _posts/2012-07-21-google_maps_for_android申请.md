---
layout: post
title: google_maps_for_android申请
category: Android开发
tags: null
---
{% include JB/setup %}
https://developers.google.com/android/maps-api-signup  
正常情况下能够进入上面的链接地址，但是下面协议条款后面本该填入key md5的地方由于种种原因不能访问了（谁让你生在TC啊！）。 如果一时找不到合适的代理，可以试试改hosts的方法来访问。具体修改方法这里不多说了，不知道的自己动手搜搜吧！  
这里说明下找到host的源地址和目的地址。  
首先cmd或terminal中敲入命令：  
nslookup mail.google.com   
返回几组地址，随便找一个Address。（我这里，2012.07.21 74.125.31.83可用）  
hosts文件末尾就加上这两行：  
74.125.31.18   apis.google.com  
74.125.31.18   google-developers.appspot.com  
保存，然后刷新dns/（win下是命令 ipconfig /flushdns, linux 下命令是 sudo networking restart (具体版本具体分析)）。  
然后重新访问<a href="https://developers.google.com/android/maps-api-signup" title="https://developers.google.com/android/maps-api-signup" target="_blank"></a>  
按步骤输入md5,接受。Generate API Key.  
-------------------------------------------------  
感谢您注册 Android 地图 API 密钥！  
您的密钥是：  
xxx  
此密钥适用于所有使用以下指纹所对应证书进行验证的应用：  
xxxxx  
下面是一个 xml 格式的示例，帮助您了解地图功能：   
      <com.google.android.maps.MapView  
                 android:layout_width="fill_parent"  
                 android:layout_height="fill_parent"  
                 android:apiKey="xxxxxxxxx"  
                 /> 