---
layout: post
title: MongoDB Schema for Angular fullstack
tags: technology  
class: post-template
subclass: 'post tag-technology'  
author: tigim
---

몽고DB 처음, AngularJS 처음, node.js 초보 ㅋㅋㅋㅋ
개삽질 중이구나~~ ㅎㅎ
Modeling이 쉽지 않다는게 느껴짐 ㅎㅎㅎ

```
var CalendarSchema = new Schema({
  type: String, /*offtime, class*/
  teacher: String,
  student: String,
  status: String, /*booked, registered, studying, done*/
  start: String,
  dow: [ { type: Number } ],
  events: [ {
    start: String,
    end: String,
    dow: [ { type: Number } ], /*only for offtime*/
    rendering: String
  } ]
});
```
