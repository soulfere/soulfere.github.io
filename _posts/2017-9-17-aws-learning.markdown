---
layout: post
title:  "AWS学习笔记" 
---

<br />

使用亚马逊AWS来部署Node.js应用。

 - Serverless架构（将应用搭载到 Amazon Lambda上）
   - 安装 Amazon CLI （Amazon的命令行应用）
   - 使用exports.myHandler = function(event, context, callback) {...}的形式重写代码
     - event中取得请求参数
     - context中取得请求的上下文（请求方式等）
     - callback函数中返回响应（如果有DynamoDB的情况，使用Arrow Function写DynamoDB自己的回调函数）
       - var dynamoDone = (req, res) => { doSomething; callback(resultValue); }
   - 在拥有证书的情况下使用CLI上传代码
   - 在Amazon控制台中编辑测试事件来测试函数的响应是否正确
 - Amazon API Gateway
   - 使用API Gateway创建API，从而自Lambda和DynamoDB搭建的后台上访问数据或执行业务逻辑
   - API Gateway的强大之处是可以对来自客户端的请求和响应进行集成与加工，从而使后台得到定制化与规范化的请求，前台可以得到定制化的响应（例如实现不同响应正文对应自定义的HTTP状态码）
   - 创建API时，可以选择与自己账户中创建的Lambda绑定，从而得到一个API地址
   - 配置API之后记得将该阶段部署（修改API之后也需要重新部署）
 - Amazon S3
   - 使用Amazon S3来管理网站的静态部分
 - CloudFront
   - 管理应用发布的网址，访问权限，允许访问规则设置等等