---
layout: post
title:  "几个简单概念辨析和理解"
---

*自己把接触到的几组概念整理一下*

---

<br />

* 跳转Servlet和跳转JSP
  - 跳转Servlet时需要配置一下Web.xml(Servlet 3.0开始支持用@WebServlet来代替Web.xml配置)．
  - 跳转JSP时不需要配置Web.xml．
* JS与ECMAScript
  - 通过ECMAScript标准，各浏览器厂商实现了自己的'JavaScript'，JavaScript，JScript都是ECMAScript的**方言**．
* StringBulider OR StringBuffer OR String
  - String是字符串常量，大量字符串拼接时会重复生成新对象，**不同字符串常量间**拼接越频繁，性能越差．
  - StringBuffer是字符串变量，不同字符串变量间拼接，被拼接对象本身可以扩充与修改，性能较好．
  - StringBuffer线程安全，StringBuilder非线程安全但是速度较前者更快．
  - StringBuilder用作StringBuffer的一个简易替换，用在字符串缓冲区被**单个线程**使用的时候．
  - StringBuilder进行带有换行的字符串拼接时，会**保持原有的换行**，而String会把一切拼到一行去．