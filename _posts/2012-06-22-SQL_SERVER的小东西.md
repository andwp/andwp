---
layout: post
title: SQL SERVER的小东西
category: SQL server
tags: [SQL , SQL server ]
---
{% include JB/setup %}
 常用的一些操作，判断表名，列名，函数，存储过程是否存在。找出有包含某个字段的所有表  
-- 判断某表中是否存在某列  
      IF EXISTS ( SELECT 1 FROM syscolumns WHERE id=OBJECT_ID(N'TableName') AND name='ColumnName')   
--判断是否存在某表  
      IF  EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID(N'TableName') AND type in (N'U'))   
--判断是否存在某存储过程  
      IF  EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[p_WF_SubmitBeforeApproval]') AND type in (N'P', N'PC'))   
 -- 判断是否存在某函数  
     IF  EXISTS (SELECT 1 FROM sys.objects WHERE object_id = OBJECT_ID(N'[dbo].[f_WF_GetNextActivityUsers_Exception_13]') AND type in (N'FN', N'IF', N'TF', N'FS', N'FT'))    
-- 找出所有包含字段名ColumnName的表  
     SELECT obj.name as TableName,col.name FROM syscolumns col INNER JOIN sys.objects obj ON obj.object_id=col.id WHERE col.name='CloumnName'    
    
--  找出约束ConstraintName属于哪个表  
     SELECT o.name AS TableName  
from  sys.key_constraints  fk  INNER JOIN sys.all_objects  o ON  fk.parent_object_id=o.object_id  
 WHERE fk.name like 'ConstraintName' 