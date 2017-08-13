---
layout: post
title:  "无JS实现图片切换"
---

**转自Pwnny's Blog**

---

<br />

HTML代码：
{% highlight html %} 

<!doctype html>
<html>
<head>
  <style>
    img {
      display: none;
      width: 100px;
      height: 100px;
    }
    
    input:checked + img {
      display: block;
    }
    
    input {
      position: absolute;
      left: -9999px;
    }
    
    label {
      cursor: pointer;
    }
  </style>
</head>
<body>
  <div id="cont">
    <input id="img1" name="img" 
    type="radio" checked="checked">
      <img src="a.png">
    <input id="img2" name="img" 
    type="radio">
      <img src="b.png">
  </div>
  <div id="nav">
    <label for="img1">First</label>
    <label for="img2">Second</label>
  </div>
</body>
</html>

{% endhighlight %} 