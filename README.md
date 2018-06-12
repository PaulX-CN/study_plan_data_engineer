# study_plan_data_engineer

首先我是自学转行的数据工程师，其次我在美国，和国内情况可能不太一样，所以给个大概的思路吧，欢迎纠正和贡献其他想法和建议。



## 一 前言：

  个人不懂网络安全方向，但感觉这一块大都是运维的部门做的（？我不确定，勿喷），这里就不献丑了。大数据方向也主要分data scientist 数据分析和 data platform 数据平台两大块。大数据分析在大公司其实还是围绕sql （加上hive上或者sparksql上操作），高端点的用神经网络，但是量级也不会太大。
对于大数据工程师来说，最主要的应该是和数据分析组合作，同时维护各种大数据pipeline和infrastructure以达到更好地提供商业性决策的目的。

这有个简单的例子 （以下英文我就不翻译了，做大数据方向应当有更强的英语阅读能力，毕竟这一块比较新，资料和新技术都是以英文为主的）：

**What you’ll do**

- **Build large-scale batch and real-time data pipelines** with data processing frameworks like Scalding, Scio, Storm, Spark and the Google Cloud Platform. 
- Leverage best practices in **continuous integration and delivery**.
- Help drive optimization, testing and tooling to **improve data quality**.
- Contributing at a senior-level to the **data warehouse design and data preparation** by implementing a solid, robust, extensible design that supports key business flows.
- Performing all of the necessary **data transformations to populate data into a warehouse table structure** that is optimized for reporting.



## 二 基础 + 工具

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


### 1） 语言： 

  首先很明确，Python和Java是绝对必须要会的两门语言，不是说这两门比其他语言好，而是因为，这两门在big data 这一块在流行程度和开放接口上来说确实是没有对手。几个最常用的工具，Hadoop Spark，Storm, Beam, Hive, Flink, Kafka, 全部都是jvm上的语言写的，Google Cloud生态圈上的技术因为亲儿子的原因会有一些go的api，但在国内基本可以不用考虑。国内的阿里云生态我不清楚，欢迎指正。

  其次也要明确，光会Python 入门尚可，行业内进阶是不太可能的。Python的定位纯粹是一个脚本语言，用来写特定的pipeline很上手，但是一旦基础库有bug，需要深入了解debug，这就必须会Java了，所以基本上所有数据工程师的职位都会要求会这两门语言。
  
  最后呢，实际工作里其实很少需要你去自己造一个轮子，但是做为一个新兴领域，documentation不全和有bug是很正常的，因此要求你必须要有自己读源码的能力，起码，单测模块必须一看就懂。
  

#### 1.1 Python 

  10分来说，Python应当最起码掌握到7分以上。7分我觉得大概是什么概念呢，首先你任何面试算法应该是可以用Python写出来的。其次应当对Python本身的细节有不错的了解了，比如一些常用的库，怎么多线程，多进程，Class的一些特别方法(__new__, __cmp__诸如此类)，迭代器，装饰器等等。
  除此以外，这个时候你应当可以较快地（个人感觉一个星期的样子？）看懂一个中小型开源项目的结构，哪些module是核心部件，互相如何调用的，需要有能够快速上手底层debug一个库的能力。
  

#### 1.2 Java

  学无止境，越熟练越好，某些库如Apache Beam是只有Java Api的（Python Api如同虚设）。能够看懂一个开源项目的底层代码实现应该是标准要求。
  

#### 1.3 Scala

  Scala是我个人很喜欢的一个语言，是我真正接触函数式编程的入门语言。同时因为这几年spark和flink变火，scala在大数据方面也有了一些应用。看个人喜好吧。



### 2） 常用库/工具/数据库 


#### 2.1 数据库

实际上你是不太可能全部用到这些技术的，个人感觉核心是各种数据库的设计和结构，比如DynamDB和BigTable 为代表的两个类型数据库的原理和实现，在这个基础上了解一些大热的几个数据库（有机会应用一下），MongoDb，Cassandra， Hbase， 还有一些常见的大型数仓，比如redshift和bigquery，关系型数据库至少要有一个比较熟练，同时了解各个数据库设计上的一些区别，比如MVCC的实现原理和一个实现的例子。

围绕着数据库还有一个重点就是Data Modeling能力，比如一个关系型数据库的设计，基本的三范式肯定要懂，但是也要知道OLAP下如何设计，还有NoSQL上的Data Modeling，denormalization的时候要尽量可以避免多余重复等等。

另外一个重点是，你必须应当**相当熟悉SQL语句的优化**！同时应该知道execution plan的工作原理。

在这个基础上，你应该相当熟悉partitioning和replication的实现和常见问题。


#### 2.2 其他 （Apache套餐）

需要熟悉主要的原理，包括Hadoop cluster 通信，HDFS读写的原理，YARN，MapReduce等。可以了解下 sqoop 迁移rdbms到Hadoop，Hive Query Language，Pig 分析等等。同时应该以Hadoop为例了解partitioning的设计以优化在HDFS上的MapReduce工作效率。

我个人认为，刚入门的工作是不太可能将你分配到架构或者cluster admin岗位的，因此大都还是写pipeline脚本，因此Spark／Flink／Beam等可以多练， MapReduce多写多练， spark/Flink 等做几个pipeline，或者自己实现一下自带的几个example。

除此以外，可以了解一下Airflow／Luigi这种ETL 管理package，工作中十分常用。


#### 2.3 零碎知识

知道几种常见的encoding，比如Avro和很常用的Protocol Buff。可以在写pipeline的时候，给自己提高难度，比如source是ProtoBuf，怎么通过kafka发／收，最终在某个数据库落地。

Docker 十分推荐学会，如果将自己的package打包，并deploy。

Jenkins 建议了解，CD／CI的关键。

### 3） 例子

最后拿我自己的技术栈做个例子：

 - redis／memcache 懂原理，做过项目，比较熟悉
 - PostgreSQL 熟悉，做过很多项目，用过MySQL，设计过
 - MongoDB／Cassandra 熟悉，做过项目
 - BigTable，懂原理，没做过实际项目。
 - Hadoop/Spark/Dataflow 熟练，做过TB级的数据流
 - BigQuery 熟练
 - Docker/Jenkins 熟练，日常工作用

## 三 学习阶段


### 1） 初级阶段


#### 1.1 阶段目标：

Python入门进阶到6分水平。接触各种类型的数据库，思考并了解各种数据库的区别和原理。

这个阶段我并不推荐做什么实际的project，首先你姿势水平不够，只能强行抄一些项目示例，其次真的抄了，你也学不到什么具体的项目逻辑，对个人提升没什么帮助。


#### 1.2 具体办法：

如果Python和Java都还没有入门，请先搜各种资料入门，比如廖雪峰的Python等等。

- 然后每天刷三道算法题，Leetcode／lintcode都可以，不懂的题目Java和Python的解法都看，争取都能阅读。Python的解法应该会写。

- 通刷sql题，完全掌握sql语句优化和写法 （hackrank等网站均可）

- 在阿里云或者本地，安装几款常见的数据库，个人推荐PostgreSQL和MongoDb，还有Redis， 学会基本的环境部署，user setup等等。

- 用Python （比如SqlAlchemy库和Pymongo库）写入一波数据到数据库。数据可以是自己用Python爬虫爬的，也可以直接搜网上公开的数据（很多大公司会有开源数据， 这有个不错的[资源](https://github.com/awesomedata/awesome-public-datasets)）。

- 思考一下用不同的数据库应该如何存储，能解决什么问题？应对什么情况？有什么好处？学会建表，并熟悉Data Modeling的知识。

- 写几个脚本，在这几个数据库之间互相倒腾 （Sql到nosql需要做什么？Nosql到Sql要做什么？什么时候可能会需要这样导出到一个完全不同的数据库？解决了什么问题？）理解不同类型数据库的优劣势。

- 思考一下如果这个时候要求分布式操作，数据库应该如何实现？试试自己搭一个分布式的MongoDb或者Cassandra？这俩原理上有什么区别？

- 随机地加大数据量，看看寻找某些特定行的时候的表现，在sql中试试加index，在nosql中试试加partition，再在sql中看看能不能加partition，nosql中能不能index？MongoDb和Cassandra都能加index吗？nosql的index和sql有什么区别？


#### 1.3 思考问题：

有数据库存在的情况下，为什么还是有很多公司将数据存储到文件系统，有什么优劣势？如果你之前下载的数据全部都存在本地文件里，怎么实现读写？会有什么问题？（提示：学习MapReduce的实现，了解HDFS和HIVE的操作）

假如要求让你用文本（txt格式）实现一个简单的数据库增删查改，该怎么做？怎么优化？会有什么问题？（提示：学习BigTable的基本原理）



### 2） 中级阶段


#### 2.1 阶段目标：

Python 十分熟练。Java从能读提升到能略写，没有Python API的时候用java api实现几个简单的项目。开始接触，阅读，理解几个大型开源库，并应用几个基本的实现。


#### 2.2 具体办法：

- 继续每天刷3道题，基本功。做完Python的看看Java的解法，试试看用Java写？了解下Java这种语言比Python强在哪里弱在哪里？这个阶段应该比较深入的了解语言底层知识，各种数据结构都应该熟练掌握，在这个基础上了解下分布式的算法，比如k个分机怎么求中位数（k路归并），怎么排序。

- 尝试配置一下Kafka，spark等环境，了解下基本的工作原理和组成部分。

- 阅读开源项目的examples并开始深入了解各个组件的调用过程。

- 将之前的数据整理（比如用protobuf／avro压缩）然后用kafka收发，先用pure python实现，再用spark／flink实现一下，这两者又有什么区别？

- 将kafka数据落地，看看目前spark／flink支持读写入什么数据库？自己能不能贡献一些代码添加一些新的IO格式？

- 将kafka数据分别落地到不同的数据库，看看操作性上有什么区别？哪个效率更高？尝试将pipeline 用docker 打包，在云上部署一下，同时本地进行读操作，看看有什么问题？

- 试试看提高你的数据量级，如果是TB级，你之前写过的所有pipeline和架构还能支撑吗？数据库还hold的住吗？探索一下各大云服务商有些什么现成的解决方案？

- 优化你的数据库！再思考一遍你会面临的实际问题。


### 3） 终极阶段

无他，贡献开源，然后写开源。
