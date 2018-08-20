---
layout: post
title:  "API Server 搭建手顺" 
---

**先用.NETCore和EFCore动手搭建个API Server Demo**

---
<br />

  - 使用新建项目向导生成 ASP.NET Core Web 应用程序
  - 之后弹出的选项中，选择``` API ```，这样我们就有一个全新的 ```API Server```
  - 使用NuGet包管理器添加下列包：
    - ```Microsoft.AspNetCore.App``` （项目生成后自带包）
    - ```Microsoft.NETCore.App```（貌似项目生成后自带包）
    - ```Microsoft.EntityFrameworkCore.Tools```
    - ```Microsoft.VisualStudio.Web.CodeGeneration.Design```
    - ```Npgsql```
    - ```Npgsql.EntityFrameworkCore.PostgreSQL```
  - 建立 ```Model``` （数据模型，对应数据库中的表）和 ```Context``` （表示与数据库的会话，并允许查询和保存实体类的实例）
    - 这里建立数据模型有两种方法，一种是手动建立与表名同名的模型类和上下文，表的字段对应模型字段，一种是通过命令自动生成Model和Context
    - 自动生成命令： ``` Scaffold-DbContext "Host=localhost;Port=5432;Database=TEST_DB;UserID=postgres;Password=postgres;" Npgsql.EntityFrameworkCore.PostgreSQL -OutputDir Models ```（这里要注意，数据库中的表要指定主键，如果表没有指定主键会报错）
  - 将生成的 ```Context``` **注入到依赖关系中**（在Startup.cs中修改ConfigureServices方法）
  - 如果需要整合到 ```Dao``` 层，就新建一个 ```Dao``` 层，如果不需要，就直接在 ```Controller``` 中使用刚才注入的 ```Context```
  - 使用时要注意，在 ```Controller``` 中要定义一个 ```private``` 变量存储```Context``` ，并在 **Controller的构造函数** 中声明```Context```
  - 调用时，将构造函数中传入的```Context```赋值给刚才创建的 ```private``` 变量，使用```private```变量的方法来进行增删查改
  - 例如查询时，使用```var myEntity = myContext.TableName.Find(pkey)```来根据主KEY查询到表的Entity
  - 根据```myEntity.myColumn```来获取字段值
  - API Server部署时，在IIS中添加允许IP，并要关闭系统防火墙（！！！）否则局域网内其他设备无法访问到应用！