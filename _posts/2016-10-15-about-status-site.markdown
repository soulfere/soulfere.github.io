---
layout: post
title:  "关于状态站"
---

*记下来关于状态站的想法（挖坑慢慢填）*

---

<br />

* 利用已有接口，用jQueryAJAX取回JSON．
* JSON跨域问题利用JSONP解决．
* 在前台JS中解析JSON．

{% highlight javascript %}
var jsonStr = JSON.stringify(json); 
var jaonObj = JSON.parse(jsonStr);  
{% endhighlight %}