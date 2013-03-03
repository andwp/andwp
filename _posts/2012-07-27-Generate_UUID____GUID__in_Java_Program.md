---
layout: post
title: Generate UUID / GUID  in Java Program
category: Android开发
tags: null
---
{% include JB/setup %}
UUID / GUID (Universally / Globally Unique IDentifier) 使用频率很高，以前只在C#里用过，不久前做的项目java里要用到。不查查看还真不知道java 里还有这个。 java里生成UUID要用到 java.util.UUID 类。  
       
import java.util.UUID;  
  
public class RandomStringUUID {  
    public static void main(String[] args) {  
        //  
        // Creating a random UUID (Universally unique identifier).  
        //  
        UUID uuid = UUID.randomUUID();  
        String randomUUIDString = uuid.toString();  
  
        System.out.println("Random UUID String = " + randomUUIDString);  
        System.out.println("UUID version       = " + uuid.version());  
        System.out.println("UUID variant       = " + uuid.variant());  
    }  
} 