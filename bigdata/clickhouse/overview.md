# ClickHouse概述
ClickHouse的全称是Click Stream,Data WareHouse，简称ClickHouse。ClickHouse 作为一个高性能 OLAP 数据库，ClickHouse从OLAP场景需求出发，定制开发了一套全新的高效列式存储引擎，并且实现了数据有序存储、主键索引、稀疏索引、数据Sharding、数据Partitioning、TTL、主备复制等丰富功能。
## 适用场景
- 1、Web和App数据分析
- 2、广告网络和RTB
- 3、电信
- 4、电子商务和金融
- 5、信息安全
- 6、监测和遥测
- 7、时序数据
- 8、商业智能
- 9、在线游戏
- 10、物联网

## 不适用场景
- 1、事物性工作（OLTP）
- 2、高并发的键值访问
- 3、Blob或者文档存储
- 4、超标准化的数据


## 优点
### 1、真正的面向列的 DBMS
ClickHouse 作为一个被设计用来在实时分析的 OLAP 组件，只是在高效率的分析方面性能发挥到极
致，那必然就会在其他方面做出取舍：
ClickHouse 是一个 DBMS，而不是一个单一的数据库。它允许在运行时创建表和数据库、加载数据和运行
查询，而无需重新配置和重新启动服务器。
### 2、数据压缩
一些面向列的 DBMS（InfiniDB CE 和 MonetDB）不使用数据压缩。但是，数据压缩确实提高了性能。
### 3、磁盘存储的数据
许多面向列的 DBMS（SAP HANA 和 GooglePowerDrill）只能在内存中工作。但即使在数千台服务器
上，内存也太小，无法在 Yandex.Metrica 中存储所有浏览量和会话。
### 4、多核并行处理
多核多节点并行化大型查询。
### 5、在多个服务器上分布式处理
在 ClickHouse 中，数据可以驻留在不同的分片上。每个分片都可以用于容错的一组副本，查询会在所有分
片上并行处理。
### 6、SQL支持
ClickHouse SQL 跟真正的 SQL 有不一样的函数名称。不过语法基本跟 SQL 语法兼容，支持 JOIN、
FROM、IN 和 JOIN 子句以及标量子查询支持子查询。
### 7、向量化引擎
数据不仅按列存储，而且由矢量 - 列的部分进行处理，这使开发者能够实现高 CPU 性能。
### 8、实时数据更新
ClickHouse 支持主键表。为了快速执行对主键范围的查询，数据使用合并树 (MergeTree) 进行递增排
序。由于这个原因，数据可以不断地添加到表中。
### 9、支持近似计算
（很多组件不具备的）统计全中国到底有多少人？1434567654 14.3E PV 近似计算UV 具体的值
该库支持为有限数量的随机密钥（而不是所有密钥）运行聚合。在数据中密钥分发的特定条件下，这提供了相
对准确的结果，同时使用较少的资源。
### 10、数据复制和对数据完整性的支持。
ClickHouse 使用异步多主复制。写入任何可用的副本后，数据将分发到所有剩余的副本。系统在不同的副
本上保持相同的数据。数据在失败后自动恢复。 扩展成为分布式的数据库OLAP引擎，严重依赖于zookeeper
的


## 参考
摘于 奈学教育-OLAP列式数据库ClickHouse