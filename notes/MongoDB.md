# MongoDB学习笔记

## 1. 数据库管理系统和 NoSQL

<div align="center"> <img src="pics/数据库/MongoDB1.jpg" width=""/> </div><br>

### 1.1 数据库管理系统
+ 数据库管理系统（英语：database management system，缩写：DBMS） 是一种针对对象数据库，为管理数据库而设计的大型电脑软件管理系统
+ 具有代表性的数据管理系统有: Oracle、Microsoft SQL Server、Access、MySQL及PostgreSQL等,通常数据库管理员会使用数据库管理系统来创建数据库系统
+ 现代DBMS使用不同的数据库模型追踪实体,属性和关系,在个人电脑,大型计算机和主机上应用最广泛的数据库管理系统是关系型DBMS,在关系型数据库模型中,用二维表格表示数据库中的数据,这些表格称为关系
+ 数据库管理系统分为两大类:RDBMS（关系型数据库）、Nosql（非关系型数据库）

#### 常见的数据库管理系统

<div align="center"> <img src="pics/数据库/MongoDB.jpg" width=""/> </div><br>

### 1.2 NoSQL

NoSQL 是对不同于传统的关系数据库的数据库管理系统的统称。

两者存在许多显著的不同点，其中最重要的是NoSQL不使用SQL作为查询语言。其数据存储可以不需要固定的表格模式，也经常会避免使用SQL的JOIN操作，一般有水平可扩展性的特征。

#### NoSQL 数据库四大家族

NoSQL中的四大家族主要是：列存储、键值、图像存储、文档存储，其类型产品主要有以下这些。

<div align="center"> <img src="pics/数据库/MongoDB1.png" width=""/> </div><br>

#### NoSQL 之间的对比

<div align="center"> <img src="pics/数据库/MongoDB3.jpg" width=""/> </div><br>

#### NoSQL 的优势

+ 高可扩展性
+ 分布式计算
+ 没有复杂的关系
+ 低成本
+ 架构灵活
+ 半结构化数据

#### NoSQL 和 RDBMS 对比
<div align="center"> <img src="pics/数据库/MongoDB2.jpg" width=""/> </div><br>

## 2. MongoDB 是什么？

MongoDB是一个文档数据库，提供好的性能，领先的非关系型数据库。采用 BSON 存储文档数据。
BSON是一种类json的一种二进制形式的存储格式，简称 Binary JSON.
相对于 json 多了 date 类型和二进制数组。

### 2.1 MongoDB 优势
+ 面向文档的存储：以 JSON 格式的文档保存数据。
+ 任何属性都可以建立索引。
+ 复制以及高可扩展性。
+ 自动分片。
+ 丰富的查询功能。
+ 快速的即时更新。

### 2.2 MongoDB 缺点
+ 多表关联： 仅仅支持 Left Outer Join
+ SQL 语句支持： 查询为主，部分支持
+ 多表原子事务： 不支持
+ 多文档原子事务：不支持
+ 16MB 文档大小限制，不支持中文排序 ，服务端 Javascript 性能欠佳
+ 无事务机制：MongoDB本身没有自带事务机制，如果需要在Mongo中实现机制，需要通过一个额外的表，从逻辑上自行实现事务。


### 2.3 MongoDB 和 关系型数据库术语对比
<div align="center"> <img src="pics/数据库/MongoDB2.png" width=""/> </div><br>

### 2.4 MongoDB 适用场景

#### 2.4.1 慎用场景
+ 高度事务性的系统：例如，银行或会计系统。传统的关系型数据库目前还是更适用于需要大量原子性复杂事务的应用程序。
+ 需要参与远程事务，或者需要跨表，跨文档原子性更新的：MongoDB 事务支持仅限于本机的单文档事务
+ 100% 写可用即任何时间写入不能停：MongoDB换主节点时候会有短暂的不可写设计所限

#### 2.4.2 适用场景
+ 网站数据：Mongo非常适合实时的插入，更新与查询，并具备网站实时数据存储所需的复制及高度伸缩性。
+ 缓存：由于性能很高，Mongo也适合作为信息基础设施的缓存层。在系统重启之后，由Mongo搭建的持久化缓存层可以避免下层的数据源 过载。
+ 大尺寸，低价值的数据：使用传统的关系型数据库存储一些数据时可能会比较昂贵，在此之前，很多时候程序员往往会选择传统的文件进行存储。
+ 高伸缩性的场景：Mongo非常适合由数十或数百台服务器组成的数据库。Mongo的路线图中已经包含对MapReduce引擎的内置支持。
+ 用于对象及JSON数据的存储：Mongo的BSON数据格式非常适合文档化格式的存储及查询。

#### 2.4.3 MongoDB 与 MySQL 的区别


||MongoDB|MySQL|
|--|--|--|
|数据库模型|非关系型|关系型|
|存储方式|虚拟内存+持久化|不同的引擎有不同的存储方式|
|查询语句|独特的MongoDB查询|传统 SQL 语句|
|架构特点|可以通过副本集，以及分片来实现高可用|常见有单点，M-S，MHA，MMM，Cluster等架构方式|
|数据处理方式|基于内存，将热数据存在物理内存中，从而达到高速读写|不同的引擎拥有其自己的特点|


【学习资料】

+ [关系型数据库与非关系型数据库的简介、对比和说明！！！](https://blog.csdn.net/Guijun6/article/details/81205767)
+ [MongoDB面试题](https://www.cnblogs.com/angle6-liu/p/10791875.html)


