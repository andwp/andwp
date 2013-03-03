---
layout: post
title: Ubuntu下安装php_Curl扩展
category: 闲
tags: null
---
{% include JB/setup %}
<shell>  
sudo apt-get install curl libcurl3 libcurl3-dev php5-curl  
</shell>  
安装完不要忘了重启apache   
<shell> sudo /etc/init.d/apache2 restart</shell>  
curl是个很强大的东东哦 