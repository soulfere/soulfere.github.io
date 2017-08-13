---
layout: post
title:  "Node.js学习笔记" 
---

<br />

公司新项目开始接触到Node.js，正好系统学习一下，以后相关的学习心得就记录在这里．

 - NPM全局安装和本地安装
   - 为了便于管理，生成工具可以全局安装，其他全部--save，生成到package.json中
 - HTTP模块
 - Node.js调试
   - Supervisor : 监视项目文件夹变更并自动重启应用更改
   - 调试是个大坑，目前使用Eclipse的Node.js插件进行
 - Express.js应用
   - Express-generator : 快速生成Node.js应用，npm包需要全局安装
     - express MyHelloWorldApp (生成项目结构，有简单欢迎页)
     - cd MyHelloWorldApp && npm install (根据package.json生成npm包的依赖关系)
     - npm start (启动应用)
   - 关于app.js
     - Node.js程序入口，请求过滤，路由处理（Express中间件的概念）
     - 解释顺序自上而下，注意请求的处理顺序
   - ORM框架
     - sequelize :  封装简单的CRUD
   - Session处理
     - express-session
   - Token应用
     - csurf
     - 使用登录时生成Token，本地利用Cookies存储，服务端利用Session存储，在CUD中，请求头中带Token，与Session中的Token进行比对
 - Jade引擎(JS模板引擎的一种，用来从JSON数据中生成HTML字符串，同类还有EJS，Handlebars等)
   - Jade在6.11.1版本的Node.js中已经不推荐使用了，打算看看EJS...
 - DynamoDB(NOSQL)
   - 使用Eclipse的AWS可视化插件
   - 默认可设两个KEY，HashKey和RangeKey
   - 配置区分地区，本地调试需要使用local版本
