?> ![](logo/redis.svg ':no-zoom')数据库

## SQL 优化

- [![](logo/wechat.svg)提高 SQL 速度的16个小技巧 | LeetCode 力扣![](logo/star.svg)](https://mp.weixin.qq.com/s/iIzOwdr82BIWrI1SWRS8dA)

## MySQL

### 查看建表语句

- [![](logo/csdn.ico ':size=16')MySQL 查看表结构的几种方式 | CSDN![](logo/star.svg)](https://blog.csdn.net/The_Best_Hacker/article/details/82794696)

如何查看数据库创建 SQL：

```sql
SHOW CREATE DATABASE `gin_demo`;
```

如何查看建表 SQL

```sql
SHOW CREATE TABLE `tb_users`;
```


### 索引

- [![](logo/wechat.svg)【面试现场】为什么MySQL数据库要用B+树存储索引？| Java3y![](logo/star.svg)](https://mp.weixin.qq.com/s/Mwh5T5wQNLrxORLpNvIZoA)
- [![](logo/codinglabs.png ':size=16')MySQL 索引背后的数据结构及算法原理 | CodingLabs![](logo/star.svg)](http://blog.codinglabs.org/articles/theory-of-mysql-index.html)
- [![](logo/csdn.ico ':size=16')Mysql学习总结（30）——MySQL 索引详解大全 | 一杯甜酒![](logo/star.svg)](https://blog.csdn.net/u012562943/article/details/52149311)

### 锁的优化

- [![](logo/wechat.svg)大牛总结的 MySQL 锁优化 | 51CTO技术栈![](logo/star.svg)](https://mp.weixin.qq.com/s/3b3y9l6vdhU4gxqMbyS3ww)

### 关键字

- [![](logo/juejin.png ':size=16')MySQL 中的 COLLATE 是什么？- horstxu | 掘金![](logo/star.svg)](https://juejin.im/post/5bfe5cc36fb9a04a082161c2)
- [![](logo/qcloud.png ':size=16')MySQL 中的 COLLATE 是什么？- horstxu | 腾讯云+社区![](logo/star.svg)](https://cloud.tencent.com/developer/article/1366841)

### 常见错误

MySQL 8.0 Error: `ER_NOT_SUPPORTED_AUTH_MODE`：

?> 参见 [MySQL 8.0 - Client does not support authentication protocol requested by server; consider upgrading MySQL client | StackOverflow](https://stackoverflow.com/questions/50093144/mysql-8-0-client-does-not-support-authentication-protocol-requested-by-server)

```sql
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password'
```

## MariaDB

## MongoDB

- [![](logo/juejin.png ':size=16')Linux Centos 7 安装 MongoDB（简单！详细！）| 掘金![](logo/star.svg)](https://juejin.im/post/5cbe73f86fb9a0320b40d687)
- [![](logo/star.svg)简明 MongoDB 入门教程 | SegmentFault](https://segmentfault.com/a/1190000010556670#articleHeader3)
- [MongoDB 教程 | 菜鸟教程](https://www.runoob.com/mongodb/mongodb-tutorial.html)
- [![](logo/wechat.svg)Python + MongoDB 小型程序利器 | Leetcode力扣](https://mp.weixin.qq.com/s/3yDyzSDzKWzoFOVfSI2-vQ)

## Redis

### 常用命令

```bash
redis-server redis.conf
redis-cli shutdown
127.0.0.1:6379> info replication
```

### 文章教程

- [![](logo/redis.svg)Redis![](logo/star.svg)](https://redis.io/)
- [![](logo/redis.svg)Try Redis![](logo/star.svg)](http://try.redis.io/)
- [![](logo/pdf.svg)Redis Cheat Sheat](https://www.cheatography.com/tasjaevan/cheat-sheets/redis/)
- [![](logo/wechat.svg)从零单排学Redis【铂金一】| Java3y](https://mp.weixin.qq.com/s/6nBUoP2cid1Qn8XngDMjJw)
- [![](logo/wechat.svg)从零单排学Redis【铂金二】| Java3y](https://mp.weixin.qq.com/s/JfARRZW9xxiPqfcPM4iAYQ)
- [![](logo/wechat.svg)Redis从入门到精通：初级篇 | 五月的仓颉](https://mp.weixin.qq.com/s/TrEcIW0DIgncpdQ00hAVSw)
- [![](logo/wechat.svg)Redis从入门到精通：中级篇 | 五月的仓颉](https://mp.weixin.qq.com/s/-qdjcKouRVfa5QtjCAZTMA)
- [![](logo/wechat.svg)10分钟写出JAVA最精简Redis客户端 | 程序猿DD![](logo/star.svg)](https://mp.weixin.qq.com/s/1ZNre_bXOh12PYQW3Fy6uA)
- [![](logo/zhihu.svg)为什么我们做分布式使用 Redis ？| 程序之心](https://zhuanlan.zhihu.com/p/50392209)
- [![](logo/oschina.ico ':size=16')为什么我们做分布式使用 Redis ？| 开源中国](https://my.oschina.net/u/3971241/blog/2221560)
- [![](logo/wechat.svg)MongoDB、HBase、Redis 等 NoSQL 优劣势、应用场景 | 芋道源码](https://mp.weixin.qq.com/s?__biz=MzUzMTA2NTU2Ng==&mid=2247485452&idx=2&sn=ac20250c11cfff7744ed877b665abcd2&chksm=fa4977bdcd3efeabcec16a46467a1073c59c2aa22db21055dab5b06d7a821a514999b9864901&mpshare=1&scene=1&srcid=1101WuCWiEn4j5I5OUJNlYp0#rd)
- [![](logo/wechat.svg)深入浅出 Redis 持久化机制 | 高可用架构![](logo/star.svg)](https://mp.weixin.qq.com/s/oe1LxgGvkQYBtoU11tYe_A)
- [![](logo/zhihu.svg)走近源码：Redis如何执行命令](https://zhuanlan.zhihu.com/p/54953927)

## LevelDB
