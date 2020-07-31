# 什么是索引？

​		回答： 索引是一种数据结构，可以进行优化sql的查询效率

# 索引为什么能够提升查询效率

​	  回答：  如果不使用索引的话，mysql 查询 会自动作全表扫描查询数据（只限myisam，Innodb不支持全表扫描，innerdb支持外键）

mysql 的索引是基于什么数据结构实现的

​    回答： 

​	 hash     只限查询单表数据，其他查询用B+tree

​	 B+tree    所有的数据都存在最底层的叶子节点上，并且所有的数据（可以假象一条数据）形成一个单链表的形式，数据（数据与数据之间形成）双向链表 有利于查询

## 	为什么选择这种数据结构？

​			二叉树在数据量比较少的时候是能够满足sql查询，但是一旦数据量大的时候，二叉树的高度就越高，查询效率就会变低

​		 红黑树，和B-（B树）也有这样的情况 ，可能比二叉树要好的多，但是mysql中不仅仅只有查询，还有增删改操作，红黑树以及b树使增删改的性能变低











使用myisam存储引擎，保存的数据信息

![image-20200707175210841](assets/image-20200707175210841.png)



而innodb  保存数据 和索引成了一个文件

得出结论： myisam 创建存储引擎是  非聚集索引   数据保存在内存中  key保存在叶子节点上 

​					innodb 创建存储引擎是聚集索引  （数据与key保存在叶子节点上）







​			索引类型

​					普通索引

​					主键索引

​					联合索引

​						有个重点 ：最左匹配原则

​								create  index inx_code_name_date  on  employ(code,name,date);												

​					全局索引



相关联的sql  



```
-- 查询数据库的默认引擎
show  ENGINES

-- 常用 搜索引擎
-- InnoDB   默认
-- MyISAM

-- 常用 搜索引擎
-- InnoDB   默认
-- MyISAM

-- 查看是否开启慢查询日志
show variables like '%slow_query_log%'
-- 开启
set global slow_query_log=1;

-- 只对当前数据库生效,如果重启后，则会失效

--  设置慢查询的阀值  

show variables like 'long_query_time'
set global long_query_time=1;
```

