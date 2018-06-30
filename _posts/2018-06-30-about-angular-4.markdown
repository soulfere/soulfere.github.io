---
layout: post
title:  "Angular学习(四)" 
---

<br />

新项目开始入坑Anaular6，从看文档开始，挖坑等填...


记录一下学习进度吧，不然感觉每天不知看了点什么，笔记记录的个人认识中可能会有错误，以后不这么菜了再来勘误。、


2018/06/30 服务


 > Service的概念

 * 实现数据层操作，负责取得数据
 * Service层一般被Component层调用
 * Service层之间可以嵌套调用
 * 和服务器通信时，Service中的方法一般返回Observable对象，后接subscribe实现异步获取数据，如果一个方法返回Observable对象但是没有subscribe，那么该请求不会发出
 * Observable对象涉及到观察者模式的概念，[相关概念](https://segmentfault.com/a/1190000008809168)
 * 服务是面向切面编程(AOP)的重要手段

 > 路由

 * 使用Angular路由模块后，使用path定义画面迁移URL，使用Component来定义定位到URL后要打开的组件
 * 当应用有多个场景时，使用路由实现
 
 > 组件和服务的关系

 * 组件中的html：值呈现
 * 组件中的ts：值传递
 * 服务：值获取