---
layout: post
title:  "大数据入坑" 
---

**开始大数据征程...**

---
<br />

 - 大数据和云计算的关系
   - 大数据是云计算非常重要的应用场景，即巨量数据，需要处理和分析，挖掘有价值的信息
   - 云计算则为大数据的处理和数据挖掘都提供了最佳的技术解决方案
 - 云计算技术
   - 服务不在本地，在服务器上（云端）
   - 云端服务器资源共享，一旦一个服务器不能承受，会把任务分配给其他机器
 - 云计算的核心
   - 云计算的核心不在开发，而在架构 —— 分布式


 - Hadoop
   - Hadoop是一个框架，由Java语言实现，可编写和运行分布式应用处理大规模数据
   - Hadoop专为离线和大规模数据分析而设计，并不适合那种对几个记录随机读写的在线事务处理模式
   - Hadoop = HDFS（文件系统，数据存储技术相关）+ MapReduce（数据处理）
   - Hadoop 2.0目前是业界主流使用的Hadoop版本
   - Hadoop的目的，是让工程师聚焦于业务实现，而不用过多操心如何把计算（或程序）变成分布式（大数据场景下，单台服务器算力不够）
   - Hadoop中，你只需要根据MapReduce的规则定义好接口方法，Hadoop会自动把相关计算分布到各个节点去
   - 假如我要做一个对大量数据的逐行筛选操作，这个操作在Hadoop中会是这样：
     - 将大量的数据导入HDFS(Hadoop Distributed FileSystem)
     - 根据定义好的MapReduce进行计算(MapReduce管理和分配计算任务，并负责将计算结果汇总)(MapReduce是第一代，作为升级版，还有Tez和Spark可以做同样的事)
     - Map —— 在各个节点上进行分布式运算
     - Reduce —— 将运算结果聚合返回
   - MapReduce的逻辑比较易懂，就是先把大活分下去，各自干完以后，汇总结果
   - MapReduce、Tez和Spark有了之后，几乎可以完成全部大数据的处理任务了，但是MapReduce的逻辑编写比较繁琐，人们期望有更高一层的抽象来简化这个过程，于是产生了Pig和Hive
     - Pig用接近脚本方式去描述MapReduce
     - Hive用SQL描述MapReduce
   - Hive出现后，你只要会用SQL描述出来数据的处理逻辑，就能进行大数据应用的编程
   - Hive是有缺点的，它在MapReduce上跑，很慢！要实时性怎么办？
   - 于是就有了Presto，Presto的出现，是为了代替MapReduce，牺牲容错，提高速度
   

 - 一个数据仓库的架构
     - 底层HDFS + MapReduce／Tez／Spark + Hive／Pig
     - 底层HDFS + Presto／Drill／Impala

 - 既然 Hive + MapReduce = Presto，那么为什么还要用Presto来调用Hive呢？



   