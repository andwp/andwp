---
layout: post
title: phonegap停止当前Media播放声音的方法
category: Android开发
tags: null
---
{% include JB/setup %}
开始搜了一些方法均无效果。后来分析了下cordova.js 的源码。找到了解决方法。  
我这里是需要在播放下一个声音的时候，关闭当前的声音,每次播放声音都是调用playsound方法。  
Media对象状态改变的时候执行onStatusCallback回调。。。  
       
   /**  
 * Andwp <pcodezui@gmail.com>  
 * http://www.andwp.net  
   */  
var soundObject = null;  
function playsound(name){  
var src = "/android_asset/www/audio/" + name + ".mp3";  
        //  存在的时候才执行stop方法  
	if (soundObject != null) {   
		soundObject.stop()  
		soundObject.release()  
	}  
	soundObject = new Media(src, onSuccess, onError, onStatusCallback, null);  
	soundObject.seekTo(0);  
	//开始播放  
	soundObject.play();  
}  
  
function onSuccess(){   
    //TODO： when success  
}  
  
function onError(){   
      // TODO: When Error  
}  
  
  
   /**   
 * @param {Object} statusCode  
 * The callback to be called when media status has changed.  
 */  
function onStatusCallback(statusCode){  
	switch(statusCode){  
   
		case Media.MEDIA_PAUSED:  
		case Media.MEDIA_STOPPED:  
			soundObject = null;  
			break;  
		default:  
			break;  
	}  
}  
 