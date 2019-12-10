# MySQL_note

## 目录

1_MySQL数据库储存位置

2_cmd下使用MySQL

3_报错 (pymysql.err.InternalError) (1366, "Incorrect string value: '\\xE7\\x9C\\x81\\xE6\\x9C\\xAC...' for column 'area' at row 1")
```
解决方法：
1. mysql -u root -p
2. use [数据库名];
3. alter table [表名] convert to character set utf8mb4;
```

4_Linux下设置MySQL的密码

https://www.cnblogs.com/snoopys/p/6129068.html

5_Linux中Mysql root用户看不到mysql库问题解决方式

https://www.cnblogs.com/owenma/p/7073297.html

6_查找指定数据库下非空的表
```sql
select * from information_schema.tables where TABLE_SCHEMA='要查询的数据库' and table_rows>0;
```

7_MySQL批量修改数据表和数据表中所有字段的字符集

https://blog.csdn.net/vfsdfdsf/article/details/90484891

8_通过生日计算年龄
```sql
SELECT TIMESTAMPDIFF(YEAR, '2000-12-22', CURDATE());
-- 18
```

