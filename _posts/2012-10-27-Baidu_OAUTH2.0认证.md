---
layout: post
title: Baidu OAUTH2.0认证
category: Android开发
tags: null
---
{% include JB/setup %}
oauth2.0 ，各个OpenAPI 的oauth2.0都应该是一样的。以前刚刚接触android的时候，搞那个新浪api，还是oauth1.0的认证。  
那个认证搞得相当的复杂，最后下了个别人提供的api，看了下签名的算法，搞得头晕晕的。。  
最近由于需要，接触了下百度开放平台的api。官方也提供了很多技术文档和Demo给用户研究。就这一点来讲，还是很不错的。  
只是百度开发文档弄得很乱，想找到自己需要的东西很不容易。。。。  
http://developer.baidu.com/wiki/index.php?title=%E5%B8%AE%E5%8A%A9%E6%96%87%E6%A1%A3%E9%A6%96%E9%A1%B5/%E7%99%BE%E5%BA%A6%E5%B8%90%E5%8F%B7%E8%BF%9E%E6%8E%A5/Mobile%E5%BA%94%E7%94%A8%E7%A8%8B%E5%BA%8F%E7%9A%84%E6%8E%88%E6%9D%83%E9%AA%8C%E8%AF%81%E6%96%B9%E6%B3%95  
对mobile的客户端开发。百度提供了详细的文档。然后用百度以前提供的开发SDK也能够直接给应用授权。我是用的无服务器的Implicit Grant授权方式，以前的SDK完成授权完全没有问题，但在百度提供的最新版的SDK却是直接打开了一了连接，困惑了一下。。  
   抱着求知的心，用jd-gui反编译了下sdk的jar包。才看明白。呵呵。原来老版本的在设置webviewClient重载的      public void onPageFinished(WebView view, String url) 有这样一段代码  
       
  if (url.contains("/login_success"))  
        {  
          Bundle values = BaiduOAuthViaDialog.this.parseUrl(url);  
  
          BaiduOAuthViaDialog.OAuthWebViewDlg.this.mListener.onComplete(values);  
          BaiduOAuthViaDialog.OAuthWebViewDlg.this.dismiss();  
        }  
   
代码很明白，当跳转的url包含了"/login_succes"这个字符的时候，就认为是授权成功了。 然后在这里回调mListener.onComplete(values);。  
剩下的就交给用户去实现了。而新版的SDK的验证是有问题的，验证是在        public boolean shouldOverrideUrlLoading(WebView view, String url)  和      public void onPageFinished(WebView view, String url)  中。。     
  不过还好，新版的sdk是提供源码的，可以自行下载后，对比老版本SDK，更改源码，编译。。。  
   
由于对WebView这个类不是很熟悉。用得极少，所以才会走这么一个弯，最近在看android框架的东西，。。。  
