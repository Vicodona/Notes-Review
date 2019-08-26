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


### 2.3 MongoDB 和 关系型数据库术语对比
<div align="center"> <img src="pics/数据库/MongoDB2.png" width=""/> </div><br>




