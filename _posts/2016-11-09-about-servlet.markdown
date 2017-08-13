---
layout: post
title:  "关于Servlet的几个小概念"
---

*很容易查到，在这里记录一下吧．*

---

<br />

* Servlet是单实例（只初始化一次）、多线程（Service方法可以处理多个客户端的请求）
* 关于Servlet拦截器，doFilter()方法拦截请求，init()方法只调用一次
* 关于Cookies
  1. 服务端创建Cookie给客户
  2. 客户下次访问时请求中带有Cookie
  3. 服务端可以从请求中取到Cookies（遍历数组）
  4. 服务端可以通过setMaxAge()，之后再response.addCookie()，这样来删除Cookie

关于重定向：

{% highlight java %}
response.setStatus
(response.SC_MOVED_TEMPORARILY)
response.setHeader
{% endhighlight %}

中文处理：

{% highlight java %}
.getBytes("ISO8859-1","UTF-8")
{% endhighlight %}