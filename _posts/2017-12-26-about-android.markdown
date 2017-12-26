---
layout: post
title:  "Android学习笔记" 
---

<br />

最近项目开始接触到，记录一些零碎的知识，以后填坑纠错。

 - 关于工具
   - Android Studio
 - 关于Layout
   - Android的View和Activity的耦合度很小，View用xml文件实现，多个View可以组合成一定的布局，即Layout
 - Activity的认识
   - Activity的切换与画面之间的传参（引入Intent声明切换的上下文，并进行Activity的切换，Bundle对象的引入方便批量传参）
 - Fragment的认识
   - 如果画面的一个位置想更换显示内容（类似微信标签页），同时又不想写多个Activity时，可以把切换的内容写成Fragment（后补代码）