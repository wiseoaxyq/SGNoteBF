---
title: sql server查询对字符串进行截取
date: 2022-08-31 14:37:30
tags: sql server
categories: note
# 加入时间线
selected: true
---
 # substring的用法
 sql server中，使用查询时，提出一个字段中的其中一部分。

 例如：我们需要将字符串'abc123efg'中的'123'提取出来，则可以用substring来实现：

 `select substring('abc123efg',4,3)`
 
 结果：'123'

### 函数解析：substring( 字段, 字段第一个字符位置, 字段截取长度)

# charindex的用法
 但是，有些时候，需求复杂，字符位置也不是固定的，长度也不固定。此时，我们可以用“charindex”这个函数来解决。
 
 charindex用于定位某个特定字符在该字符串中的位置。

### 函数解析：charindex( '特定字符', 字段名称 )