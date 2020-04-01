# MySQL_note

## 目录

#### 1_MySQL数据库储存位置

#### 2_cmd下使用MySQL

#### 3_报错 (pymysql.err.InternalError) (1366, "Incorrect string value: '\\xE7\\x9C\\x81\\xE6\\x9C\\xAC...' for column 'area' at row 1")
```
解决方法：
1. mysql -u root -p
2. use [数据库名];
3. alter table [表名] convert to character set utf8mb4;
```

#### 4_Linux下设置MySQL的密码

https://www.cnblogs.com/snoopys/p/6129068.html

#### 5_Linux中Mysql root用户看不到mysql库问题解决方式

https://www.cnblogs.com/owenma/p/7073297.html

#### 6_查找指定数据库下非空的表
```sql
select * from information_schema.tables where TABLE_SCHEMA='要查询的数据库' and table_rows>0;
```

#### 7_MySQL批量修改数据表和数据表中所有字段的字符集

https://blog.csdn.net/vfsdfdsf/article/details/90484891

#### 8_通过生日计算年龄
```sql
SELECT TIMESTAMPDIFF(YEAR, '2000-12-22', CURDATE());
-- 18
```

#### 9_使用查询(select)结果插入(insert)

MySql将查询结果插入到另外一张表 https://www.cnblogs.com/qlqwjy/p/8351655.html

#### 10_使用查询(select)结果更新(update)

MySql通过查询结果集更新数据 https://segmentfault.com/a/1190000018568782

mysql update select 从查询结果中更新数据 https://www.cnblogs.com/deepalley/p/11018918.html

mysql将查询结果更新到表中 https://blog.csdn.net/qq_41563799/article/details/90217753

#### 11_通过时间过滤筛选

mysql的时间条件筛选 https://blog.csdn.net/Yuan52007298/article/details/81584716

#### 12_报错"Got a packet bigger than 'max_allowed_packet' bytes"

解决mysql执行SQL文件，报错："Got a packet bigger than 'max_allowed_packet' bytes" https://blog.csdn.net/github_39325328/article/details/79549756

#### 13_shell脚本定时备份MySQL数据库

MySQL数据库定时备份的实现方法 https://www.jb51.net/article/158812.htm

实战-MySQL定时全量备份（1） https://blog.csdn.net/zone_/article/details/81293131

#### 14_MySQL定时任务

#### 15_MySql用户访问权限的设置

https://www.jianshu.com/p/1b17442edd38

#### 16_MYSQL导出表结构（含列名、数据类型、字段备注注释）导出成Excel

https://blog.csdn.net/liu_yulong/article/details/92767596

```sql
SELECT
	COLUMN_NAME 列名,
	COLUMN_TYPE 数据类型,
	DATA_TYPE 字段类型,
	CHARACTER_MAXIMUM_LENGTH 长度,
	IS_NULLABLE 是否为空,
	COLUMN_DEFAULT 默认值,
	COLUMN_COMMENT 备注 
FROM
	information_schema.COLUMNS 
WHERE
	TABLE_NAME = 'my_table_name' -- 表名
	
	AND TABLE_SCHEMA = 'my_db_name' -- 数据库名
```

#### 17_报错"ERROR 1215 (HY000) at line 1811: Cannot add foreign key constraint"

mysql执行带外键的sql文件时出现mysql ERROR 1215 (HY000): Cannot add foreign key constraint的解决 https://www.cnblogs.com/liushui-sky/p/8830936.html

#### 18_Navicat设置字段的唯一性（UNIQUE）

Navicat Premium怎么设置字段的唯一性（UNIQUE） https://blog.csdn.net/Song_JiangTao/article/details/82192189
