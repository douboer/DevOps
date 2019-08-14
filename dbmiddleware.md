## 数据库中间件

:question:
- 读写分离，&效率
- 分库分表，切分能力
- HA能力
- 并发性
- 稳定性
- 可维护性
- 社区活跃度，开源持续维护

* [myCat note](mycat.md)


mycat|cobar|Atlas|TDDL|heisenberg|Oceanus|vitess|OneProxy
Mycat与以上中间件的对比如下表所示。
对比项目|[mycat](https://github.com/MyCATApache/Mycat-doc)|Mango|Cobar|Heisenberg|[Atlas](https://github.com/Qihoo360/Atlas/blob/master/README_ZH.md)|Amoeba
----|-----|-----|----|----------|----|----
公司|阿里| |阿里|百度|360|
数据切片|支持|支持|支持|支持|支持|支持
读写分离|支持|支持|支持|支持|支持|支持
宕机自动切换|支持|不支持|支持|不支持|半支持，影响写|不支持
MySQL协议|前后端支持|JDBC|前端支持|前后端支持|前后端支持|JDBC
支持的数据库|MySQL、Oracle、MongoDB、PostgreSQL|MySQL|MySQL|MySQL|MySQL|MySQL、MongoDB
社区活跃度|高|活跃|停滞|低|中等|停滞
文档资料|极丰富|较齐全|较齐全|缺少|中等|缺少
是否开源|开源|开源|开源|开源|开源|开源
是否支持事务|弱XA|支持|单库强一致、分布式弱事务|单库强一致、多库弱事务|单库强一致、分布式弱事务|不支持


DAL
MySQL DAL（Data Access Layer）数据访问层

分表：如UID mod 2分2张表存储，查询时同样操作

