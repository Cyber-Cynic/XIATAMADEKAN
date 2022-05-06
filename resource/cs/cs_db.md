### 关系型数据库 vs 非关系性数据库？

### 范式？
数据库范式，又称为数据库规范化，用于保证数据库之间的关系合理，减少数据库中的数据冗余，消除操作带来的异常，增进数据的一致性。  

### SQL执行过程？
![sqlexe](https://img-blog.csdnimg.cn/20200727195951575.png)

### SQL查询顺序？
![sqlorder](https://i.stack.imgur.com/6YuwE.jpg)

### B-Tree（B树）
![btree](https://www.baeldung.com/wp-content/uploads/sites/4/2020/05/btreefull-3.png)

![bplustree](https://www.baeldung.com/wp-content/uploads/sites/4/2020/05/bplustreefull-2.png)

区别：
1. B+trees allow satellite data to be stored in leaf nodes only, whereas B-trees store data in both leaf and internal nodes
2. In B+trees, data stored on the leaf node makes the search more efficient since we can store more keys in internal nodes – this means we need to access fewer nodes
3. Deleting data from a B+tree is easier and less time consuming because we only need to remove data from leaf nodes
4. Leaf nodes in a B+tree are linked together making range search operations efficient and quick

参考：
https://www.baeldung.com/cs/b-trees-vs-btrees

### 索引？
1. 主键索引:每个表一个主键
2. 唯一索引：索引列的所有值都只能出现一次，即必须唯一，值可以为空。
3. 普通索引：没有唯一性的限制。
4. 全文索引：

### 索引的好处和坏处？
好处：DB按照某个算法生成一个索引文件，在查询数据库时，找到索引文件进行遍历(折半查找大幅查询效率)
坏处：产生索引文件的，占用磁盘空间。索引文件是一个二叉树类型的文件，我们的dml操作同样也会对索引文件进行修改，所以性能会下降

### 索引创建的
1. 较频繁的作为查询条件字段应该创建索引
2. 唯一性太差的字段不适合创建索引，尽管频繁作为查询条件，例如gender性别字段
3. 更新非常频繁的字段不适合作为索引
4. 不会出现在where子句中的字段不该创建索引

### 存储过程？
1. 效率高：存储过程编译一次后，就会存到数据库，每次调用时都直接执行。
2. 降低网络流量：远程调用时，不会传输大量的字符串类型的sql语句。
3. 复用性高：存储过程往往是针对一个特定的功能编写的，当再需要完成这个特定的功能时，可以再次调用该存储过程。
4. 可维护性高：当功能要求发生小的变化时，修改之前的存储过程比较容易，花费精力少。
5. 安全性高：完成某个特定功能的存储过程一般只有特定的用户可以使用，具有使用身份限制，更安全。

但是分库分表、微服务时代，不推荐使用。千万般的好，抵不过不好扩展这一项。

### 函数？
存储过程和函数存在以下几个区别：  
1）一般来说，存储过程实现的功能要复杂一点，而函数的实现的功能针对性比较强。存储过程，功能强大，可以执行包括修改表等一系列数据库操作；用户定义函数不能用于执行一组修改全局数据库状态的操作。  

2）对于存储过程来说可以返回参数，如记录集，而函数只能返回值或者表对象。函数只能返回一个变量；而存储过程可以返回多个。存储过程的参数可以有IN,OUT,INOUT三种类型，而函数只能有IN类~~存储过程声明时不需要返回类型，而函数声明时需要描述返回类型，且函数体中必须包含一个有效的RETURN语句。  

3）存储过程，可以使用非确定函数，不允许在用户定义函数主体中内置非确定函数。  

4）存储过程一般是作为一个独立的部分来执行（ EXECUTE 语句执行），而函数可以作为查询语句的一个部分来调用（SELECT调用），由于函数可以返回一个表对象，因此它可以在查询语句中位于FROM关键字的后面。 SQL语句中不可用存储过程，而可以使用函数。  

### 触发器？
触发器（trigger）是SQL server 提供给程序员和数据分析员来```保证数据完整性```的一种方法，它是与表事件相关的特殊的```存储过程```，它的执行不是由程序调用，也不是手工启动，而是由```事件```来触发，比如当对一个表进行操作（ insert，delete， update）时就会激活它执行。

### 联查
![sqljoin](https://i.redd.it/dyqnzpuddxk21.png)

### in vs exists?
https://stackoverflow.com/questions/24929/difference-between-exists-and-in-in-sql

### 全局变量？
SQLServer 使用@@  
https://stackoverflow.com/questions/29671417/what-is-the-usage-of-in-sql-server/29677916

### where vs on?
1. Does not matter for inner joins
2. Matters for outer joins  
    a. WHERE clause: After joining. Records will be filtered after join has taken place.  
    b. ON clause - Before joining. Records (from right table) will be filtered before joining. This may end up as null in the result (since OUTER join).    

https://stackoverflow.com/questions/354070/sql-join-where-clause-vs-on-clause

### 事务
1. Atomicity（原子性）：一个事务（transaction）中的所有操作，或者全部完成，或者全部不完成，不会结束在中间某个环节。事务在执行过程中发生错误，会被回滚（Rollback）到事务开始前的状态，就像这个事务从来没有执行过一样。即，事务不可分割、不可约简。
2. Consistency（一致性）：在事务开始之前和事务结束以后，数据库的完整性没有被破坏。这表示写入的资料必须完全符合所有的预设约束、触发器、级联回滚等。
3. Isolation（隔离性）：数据库允许多个并发事务同时对其数据进行读写和修改的能力，隔离性可以防止多个事务并发执行时由于交叉执行而导致数据的不一致。事务隔离分为不同级别，包括未提交读（Read uncommitted）、提交读（read committed）、可重复读（repeatable read）和串行化（Serializable）。
4. Durability（持久性）：事务处理结束后，对数据的修改就是永久的，即便系统故障也不会丢失。

### No-SQL
强调键-值存储和面向文档数据库的优点，而不是单纯的反对RDBMS

### 分库分表
引发的问题  
1. 在执行了分库之后，难以避免会将原本逻辑```关联性```很强的数据划分到不同的表、不同的库上，这时，表的关联操作将受到限制，我们多数情况下无法join位于不同分库的表（因为多数公司都明令禁止跨库sql），结果原本一次查询能够完成的业务，可能需要多次查询才能完成。

2. 原来在单体DB环境下，可以用DB的```事务```来保证一些操作的原子操作，但是在分散到多个数据库的情况下，统一管理这些操作变的困难。虽然一些大厂提供的也有跨库的事务解决方案，但是性能上实在是差强人意，所以在很多情况下并不实用。比如上边提到的商品库存支付，在单体应用的情况下，三个业务在同一个数据库，当发生支付业务，更改商品库存和更新订单状态这两个操作可以利用数据库提供的事物来完成，而且性能在可接受范围之内，如果这三个业务分布在不同的数据库，有几率会发生只执行其中一个操作的情况发生，其实这也是分布式事物要解决的问题。在很多情况下，分布式事物是无法避免的，根据业务综合情况适当采用分布式事物也是一种有效的解决方案，最坏的情况下，可能需要人工介入了。

3. 分库对于DBA来说意味着```工作量```的成倍增加，原来只需要管理一个DB，现在却要管理N个DB，而且每个DB都需要备份，监控，甚至做高可用，扩展等工作。原来可能只需要一个DBA管理人员，分库之后可能会需要两个甚至三个，导致了公司在人力投入上的加大。  

https://xie.infoq.cn/article/ee41e234529bb31ab1de4c69b  
https://xie.infoq.cn/article/378822829ef1a4563683b5e0e