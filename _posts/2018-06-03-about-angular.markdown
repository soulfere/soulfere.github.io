---
layout: post
title:  "Angular学习(一)" 
---

<br />

新项目开始入坑Anaular6，从看文档开始，挖坑等填...


记录一下学习进度吧，不然感觉每天不知看了点什么，笔记记录的个人认识中可能会有错误，以后不这么菜了再来勘误。、


2018/06/25 正式开始看Angular官网（Angular.io）


 > src文件夹

 * 组件的概念（一个组件一般由 ts/html/css/spec.ts 四个文件组成）
 * module.ts 负责把组件装配起来，根模块，在此处声明组件
 * assets/* 资源文件夹，放图片、视频等等资源
 * environments/* 环境配置文件，可以给开发环境、测试环境和生产环境写多套配置文件，以应对项目部署位置不同、是否使用mock模块等等的变化，构建应用时可以即时切换
 * browserslist 不同前端工具共用目标浏览器（不是很懂..浏览器适配用的么？看下面貌似polifills.ts是处理浏览器兼容性的）
 * favicon.ico 网站标签页图标
 * index.html 应用主页，感觉和大多模板语言类似，主页是应用构建后自动生成的，应该在页面生成之前就确定页面的内容、样式、行为，生成后不应该再手动改变页面的内容，此页面内也不该硬写任何 ```<script>``` 或者 ```<link>``` 标签
 * karma.conf.js 单元测试配置文件，[相关简介](https://karma-runner.github.io/)
 * main.ts 应用的主入口，编译应用程序，引导根模块在浏览器中运行(那么这样看起来，module.ts和main.ts加起来类似于express.js中的app.js)
 * polyfills.ts 处理浏览器兼容性
 * styles.css 全局CSS文件，定义一些全局的基础样式，和组件有关的样式还是定义在组件中比较好
 * test.ts 单元测试入口
 * tsconfig.{app|spec}.json Angular程序TypeScript编译器配置文件（前者是程序，后者是测试）
 * tslint.json 用来保持代码风格一致（不是很懂，写的不规范的地方报警告还是直接编译不通过？是单独运行用来进行全局的代码风格检查？还是自动把代码整洁化？）


 > root文件夹（除src文件夹之外的其他文件，都是帮助构建应用的文件，与应用内容无关联）

 * e2e/ 端到端测试用，该测试环境与应用隔离，所以放到了src外面
 * node_modules/ 放第三方npm包
 * .editorconfig 编辑器配置，可以用来统一开发者的编辑器配置，方便协同开发，支持主流编辑器（还没试过）
 * .gitignore git排除在版本管理之外的文件
 * angular.json Angular命令行工具的配置文件
 * package.json 引用的第三方包
 * protractor.conf.js Protractor测试工具的配置文件
 * README.md README文件
 * tsconfig.json  IDE的TypeScript编译器的配置文件
 * tslint.json 功能同src文件夹的对应文件，这个更基础，上面那个相当于额外配置