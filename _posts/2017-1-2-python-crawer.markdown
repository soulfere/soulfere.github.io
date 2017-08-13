---
layout: post
title:  "简单的Python爬虫" 
---

<br />

今天看了一下爬虫的相关知识，在Github上看见几个Java的爬虫项目，不过有点难以理解。

于是打算从Python爬虫开始了解。

涉及到的概念与工具：

1. [Anaconda:](https://www.continuum.io) 一个Python开发的数据分析平台
2. [The Jupyter Notebook:](http://jupyter.org/) 一个交互式笔记本
3. [BeautifulSoup:](https://www.crummy.com/software/BeautifulSoup/) 一个Python库

下面的一段演示代码从新浪新闻的HTML中取到一些新闻标题，然后进行格式化处理：

{% highlight python %}
import requests
from bs4 import BeautifulSoup
res = requests.get
('http://news.sina.com.cn/china/')
res.encoding = 'UTF-8'
soup = 
BeautifulSoup(res.text,'html.parser')
for news in soup.select('.blk121'):
  for i in range(len(news.select('a'))):
    title = news.select('a')[i].text
    link  = news.select('a')[i]['href']
    print (title,link)
{% endhighlight %}

对于无法直接从HTML中找到的信息，从控制台的JS中找到对应的HTTP请求字符串。
对于复杂的响应信息，要学会把JSON转成字典，以便筛出有用的信息：
{% highlight python %}
import json
jsondata = json.loads(news)
jsondata['result']['count']['total']
{% endhighlight %}

对于可变的项目，可以在原来的字符串中使用{}挖掉一部分，再利用字符串的format方法填入。