# study_plan_data_engineer

首先我是自学转行的数据工程师，其次我在美国，和国内情况可能不太一样，所以给个大概的思路吧。



## 前言：

  个人不懂网络安全方向，但感觉这一块大都是运维的部门做的（？我不确定，勿喷），这里就不献丑了。大数据方向也主要分data scientist 数据分析和 data platform 数据平台两大块。大数据分析在大公司其实还是围绕sql （加上hive上或者sparksql上操作），高端点的用神经网络，但是量级也不会太大。
对于大数据工程师来说，最主要的应该是和数据分析组合作，同时维护各种大数据pipeline和infrastructure以达到更好地提供商业性决策的目的。

这有个简单的例子 （以下英文我就不翻译了，做大数据方向应当有更强的英语阅读能力，毕竟这一块比较新，资料和新技术都是以英文为主的）：

**What you’ll do**

- **Build large-scale batch and real-time data pipelines** with data processing frameworks like Scalding, Scio, Storm, Spark and the Google Cloud Platform. 
- Leverage best practices in **continuous integration and delivery**.
- Help drive optimization, testing and tooling to **improve data quality**.
- Contributing at a senior-level to the **data warehouse design and data preparation** by implementing a solid, robust, extensible design that supports key business flows.
- Performing all of the necessary **data transformations to populate data into a warehouse table structure** that is optimized for reporting.


## 基础 + 工具

先贴个比较常见的数据工程师的jd吧（这是mid 到senior level的，但是贴出来用作我们的学习目标）：

**Who you are**

- You know how to work with high volume heterogeneous data, preferably with distributed systems such as Hadoop, BigTable, and Cassandra. 
- You are knowledgeable about data modeling, data access, and data storage techniques in a Data warehousing context.
- Able to write, analyze, and debug SQL queries
- You care about agile software processes, data-driven development, reliability, and responsible experimentation.
- Experience with at least one scripting language (Shell, Python, Perl etc.)
- Experience with an OO programming language like Java.

**Preferred Qualifications**
- Experience working extensively in multi-petabyte DW environment
- Experience in engineering large-scale systems in a product environment
- Experience with Data Warehouse design, ETL (Extraction, Transformation & Load), architecting efficient software designs for DW platform.
- Knowledge of NoSQL stores is a plus
- Experienced in implementing data warehouses with MPP databases like Teradata. [is a plus]
- Ideal candidates will have a deep understanding of technical and functional designs for Databases, Data Warehousing, Reporting, and Data Mining areas
- Passion for about continuous learning, experimenting, applying and contributing towards cutting edge open source Big Data technologies and software paradigms

下面分块来详细说。

### 语言： 

  首先很明确，Python和Java是绝对必须要会的两门语言，不是说这两门比其他语言好，而是因为，这两门在big data 这一块在流行程度和开放接口上来说确实是没有对手。几个最常用的工具，Hadoop Spark，Storm, Beam, Hive, Flink, Kafka, 全部都是jvm上的语言写的，Google Cloud生态圈上的技术因为亲儿子的原因会有一些go的api，但在国内基本可以不用考虑。国内的阿里云生态我不清楚，欢迎指正。

  其次也要明确，光会Python 入门尚可，行业内进阶是不太可能的。Python的定位纯粹是一个脚本语言，用来写特定的pipeline很上手，但是一旦基础库有bug，需要深入了解debug，这就必须会Java了，所以基本上所有数据工程师的职位都会要求会这两门语言。
  
  最后呢，实际工作里其实很少需要你去自己造一个轮子，但是做为一个新兴领域，documentation不全和有bug是很正常的，因此要求你必须要有自己读源码的能力，起码，单测模块必须一看就懂。

#### Python 

  10分来说，Python应当最起码掌握到7分以上。7分我觉得大概是什么概念呢，首先你任何面试算法应该是可以用Python写出来的。其次应当对Python本身的细节有不错的了解了，比如一些常用的库，怎么多线程，多进程，Class的一些特别方法(__new__, __cmp__诸如此类)，迭代器，装饰器等等。
  除此以外，这个时候你应当可以较快地（个人感觉一个星期的样子？）看懂一个中小型开源项目的结构，哪些module是核心部件，互相如何调用的，需要有能够快速上手底层debug一个库的能力。

#### Java

  学无止境，越熟练越好，某些库如Apache Beam是只有Java Api的（Python Api如同虚设）。能够看懂一个开源项目的底层代码实现应该是标准要求。

#### Scala

  Scala是我个人很喜欢的一个语言，是我真正接触函数式编程的入门语言。同时因为这几年spark和flink变火，scala在大数据方面也有了一些应用。看个人喜好吧。

### 常用库/工具/数据库 

实际上你是不太可能全部用到这些技术的，个人感觉核心是各种数据库的设计和结构，比如DynamDB和BigTable 为代表的两个类型数据库的原理和实现，在这个基础上了解一些大热的几个数据库（有机会应用一下），MongoDb，Cassandra， Hbase， 还有一些常见的大型数仓，比如redshift和bigquery，关系型数据库至少要有一个比较熟练，同时了解各个数据库设计上的一些区别，比如MVCC的实现原理和一个实现的例子。

围绕着数据库还有一个重点就是Data Modeling能力，比如一个关系型数据库的设计，基本的三范式肯定要懂，但是也要了解OLAP下如何设计，还有NoSQL上的Data Modeling，denormalization的时候要尽量可以避免多余重复。

拿我自己的技术栈做个例子：

 - redis／memcache 懂原理，做过项目，比较熟悉
 - PostgreSQL 熟悉，做过很多项目，用过MySQL，设计过
 - MongoDB／Cassandra 熟悉，做过项目
 - BigTable，懂原理，没做过实际项目。
 - Hadoop/Spark/Dataflow 熟练，做过PB级的数据流
 - BigQuery 熟练

除了数据库以外

1. Apache 套餐： Hadoop/Spark/Flink/Storm/Beam

需要熟悉主要的原理，包括Hadoop cluster 通信，HDFS读写的原理，YARN，MapReduce等。可以了解下 sqoop 迁移rdbms到Hadoop，Hive Query Language，Pig 分析等等。同时应该以Hadoop为例了解partitioning的设计以优化在HDFS上的MapReduce工作效率。

Spark



## 初级阶段

## 中级阶段

## 终极阶段
