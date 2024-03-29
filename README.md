# MySQL_note

## 目录

1. #### MySQL数据库储存位置

2. #### cmd下使用MySQL

3. #### 报错 (pymysql.err.InternalError) (1366, "Incorrect string value: '\\xE7\\x9C\\x81\\xE6\\x9C\\xAC...' for column 'area' at row 1")

   ```
   解决方法：
   1. mysql -u root -p
   2. use [数据库名];
   3. alter table [表名] convert to character set utf8mb4;
   ```

4. #### MySQL用户管理

   MySQL用户管理：添加用户、授权、删除用户 https://www.cnblogs.com/pejsidney/p/8945934.html

   MySql用户访问权限的设置 https://www.jianshu.com/p/1b17442edd38

   Mysql_修改root用户密码 https://www.cnblogs.com/wodexk/p/10674636.html

   MySQL设置root密码 https://www.cnblogs.com/snoopys/p/6129068.html

5. #### Linux中Mysql root用户看不到mysql库问题解决方式

   https://www.cnblogs.com/owenma/p/7073297.html

6. #### 查找指定数据库下非空的表

   ```sql
   select * from information_schema.tables where TABLE_SCHEMA='要查询的数据库' and table_rows>0;
   ```

7. #### MySQL批量修改数据表和数据表中所有字段的字符集

   https://blog.csdn.net/vfsdfdsf/article/details/90484891

8. #### 通过生日计算年龄

   ```sql
   SELECT TIMESTAMPDIFF(YEAR, '2000-12-22', CURDATE());
   -- 18
   ```

9. #### 使用查询(select)结果插入(insert)

   [MySql将查询结果插入到另外一张表](https://www.cnblogs.com/qlqwjy/p/8351655.html)

10. #### 使用查询(select)结果更新(update)

    [MySql通过查询结果集更新数据](https://segmentfault.com/a/1190000018568782)

    [mysql update select 从查询结果中更新数据](https://www.cnblogs.com/deepalley/p/11018918.html)

    [mysql将查询结果更新到表中](https://blog.csdn.net/qq_41563799/article/details/90217753)

11. #### 通过时间过滤筛选

    [mysql的时间条件筛选](https://blog.csdn.net/Yuan52007298/article/details/81584716)

12. #### 报错"Got a packet bigger than 'max_allowed_packet' bytes"

    [解决mysql执行SQL文件，报错："Got a packet bigger than 'max_allowed_packet' bytes"](https://blog.csdn.net/github_39325328/article/details/79549756)

13. #### shell脚本定时备份MySQL数据库

    [MySQL数据库定时备份的实现方法](https://www.jb51.net/article/158812.htm)

    [实战-MySQL定时全量备份](https://blog.csdn.net/zone_/article/details/81293131)

14. #### MySQL定时任务

15. #### MYSQL导出表结构（含列名、数据类型、字段备注注释）导出成Excel

    https://blog.csdn.net/liu_yulong/article/details/92767596

    ```sql
    SELECT
    	COLUMN_NAME 列名,
    	COLUMN_TYPE 数据类型,
    	DATA_TYPE 字段类型,
    	CHARACTER_MAXIMUM_LENGTH 长度,
    	COLUMN_KEY 键,
    	IS_NULLABLE 是否为空,
    	COLUMN_DEFAULT 默认值,
    	COLUMN_COMMENT 备注 
    FROM
    	information_schema.COLUMNS 
    WHERE
    	TABLE_NAME = 'my_table_name' -- 表名
    	
    	AND TABLE_SCHEMA = 'my_db_name' -- 数据库名
    ```

16. #### 报错"ERROR 1215 (HY000) at line 1811: Cannot add foreign key constraint"

    [mysql执行带外键的sql文件时出现mysql ERROR 1215 (HY000): Cannot add foreign key constraint的解决](https://www.cnblogs.com/liushui-sky/p/8830936.html)

17. #### Navicat设置字段的唯一性（UNIQUE）

    [Navicat Premium怎么设置字段的唯一性（UNIQUE）](https://blog.csdn.net/Song_JiangTao/article/details/82192189)

18. #### 报错"Index column size too large. The maximum column size is 767 bytes."

    https://blog.51cto.com/zhaowl/2324758

    https://blog.csdn.net/hanyunpiaoyu/article/details/82377897

19. #### 设置max_allowed_packet为256M

    ```
    可解决的报错1：
    Error Code: 2006 - MySQL server has gone away
    
    可解决的报错2：
    Variable 'time_zone' can't be set to the value of 'NULL'
    ```

    ```
    mysql> SET GLOBAL max_allowed_packet=1024 * 1024 * 256;
    Query OK, 0 rows affected (0.07 sec)
    
    mysql> exit;
    
    mysql> show variables like 'max_allowed_packet';
    +--------------------+-----------+
    | Variable_name      | Value     |
    +--------------------+-----------+
    | max_allowed_packet | 268435456 |
    +--------------------+-----------+
    1 row in set (0.09 sec)
    ```

    https://blog.csdn.net/sunny05296/article/details/80446944

    https://blog.csdn.net/remzhang/article/details/88883440

    http://www.voidcn.com/article/p-rpuiipug-bsd.html

20. #### 限制用户登录频率防暴力破解`connection_control.so`

    [MySQL会话控制限制登录次数](https://www.cnblogs.com/pettyfer/p/12263732.html)

    [mysql限制登录次数以及重试时间](https://www.cnblogs.com/hantwo-cn/p/13398328.html)

21. #### 报错"Error updating database. Cause: java.sql.SQLSyntaxErrorException: The size of BLOB/TEXT data inserted in one transaction is greater than 10% of redo log size. Increase the redo log size using innodb_log_file_size."

    https://itdiandi.net/view/572

    https://blog.csdn.net/jian876601394/article/details/104823636

    ```
    主要和 innodb_log_file_size, max_allowed_packet 两参数有关
    mysql> show variables like "%innodb_log_file_size%";
    mysql> show variables like "%max_allowed_packet%";
    ```

22. #### MySQL服务命令

    ```shell
    # 指定配置文件，启动MySQL
    [root@myserver ~]$ mysqld --defaults-file=/usr/my.cnf --user=root
    
    # 指定配置文件，以服务形式启动MySQL
    [root@myserver ~]$ service mysql start --defaults-file=/usr/my.cnf --user=root
    # 查看MySQL状态
    [root@myserver ~]$ service mysql status
    # 停止MySQL
    [root@myserver ~]$ service mysql stop
    ```

23. #### MySQL配置文件详解

    [MySQL指定mysqld启动时所加载的配置文件](https://www.cnblogs.com/jeffen/p/5998083.html)

24. #### 二叉树前序遍历、中序遍历、后序遍历、层序遍历

    | 遍历方式        | 实现              | 应用                                   |
    | --------------- | ----------------- | -------------------------------------- |
    | 前序遍历（DLR） | 递归/栈（非递归） | 爬虫深度优先遍历                       |
    | 中序遍历（LDR） | 递归/栈（非递归） | 中序遍历BST得到BST所有节点值的顺序输出 |
    | 后序遍历（LRD） | 递归/栈（非递归） |                                        |
    | 层序遍历        | 队列（先进先出）  | 爬虫广度优先遍历                       |

    [二叉树前序遍历、中序遍历、后序遍历、层序遍历的直观理解](https://blog.csdn.net/u013834525/article/details/80421684)

    [二叉树、前序遍历、中序遍历、后序遍历](https://www.cnblogs.com/lanhaicode/p/10358736.html)

    [树的前序遍历、中序遍历、后序遍历详解](https://www.cnblogs.com/jpfss/p/11141956.html)

    [二叉树的Python实现](https://www.jianshu.com/p/9503238394df)

25. #### 二叉树、红黑树

    [漫画：红黑树杀人事件始末](https://mp.weixin.qq.com/s/r6foXjNHmU0l_fzrMqxG7Q)

    > 二叉树概念、查找、插入、删除，
    >
    > 红黑树概念、旋转操作（左旋、右旋）、插入、删除、插入修正操作及原理、删除修正操作及原理。

26. #### B树、B+树、B*树

    [B树、B+树详解](https://www.cnblogs.com/lianzhilei/p/11250589.html)

    [彻底搞懂系列B-树、B+树、B-树、B*树](https://blog.csdn.net/chai471793/article/details/99563704)

    [漫画：什么是B+树？](https://zhuanlan.zhihu.com/p/54102723)

27. [MySQL索引类型 ](https://www.cnblogs.com/luyucheng/p/6289714.html)

    1. 普通索引
    2. 唯一索引
    3. 主键索引
    4. 组合索引
    5. 全文索引

28. [MySQL索引原理以及查询优化](https://www.cnblogs.com/bypp/p/7755307.html)

29. #### SQL语句执行顺序

    > FROM - ON - JOIN - **WHERE** - GROUP BY - WITH - **HAVING** - **SELECT** - DISTINCT - ORDER BY - LIMIT

    ```
    (8)  SELECT    (9)  DISTINCT
    (1)  FROM
    (3)   JOIN
    (2)     ON
    (4)  WHERE
    (5)  GROUP BY
    (6)  WITH {CUBE|ROLLUP}
    (7)  HAVING
    (10) ORDER BY
    (11) LIMIT
    ```
   
    ```sql
    mysql> -- 求每个部门的平均工资,以及剔除薪资低于1000的人员之后的平均工资
    mysql> -- 2个临时表的定时语句通过with封装成子查询了，程序可读性增强
    mysql> with tmp1 as
        ->  (select e1.deptno, round(avg(ifnull(e1.sal, 0)), 2) avg_sal
        ->    from emp e1
        ->    group by e1.deptno),
        -> tmp2 as
        ->  (select e1.deptno, round(avg(ifnull(e1.sal, 0)), 2) avg_sal
        ->    from emp e1
        ->    where e1.sal > 1000
        ->    group by e1.deptno)
        -> select d.deptno, tmp1.avg_sal avg_sal1, tmp2.avg_sal avg_sal2
        ->   from dept d
        ->   left join tmp1
        ->     on d.deptno = tmp1.deptno
        ->   left join tmp2
        ->     on d.deptno = tmp2.deptno;
    +--------+----------+----------+
    | deptno | avg_sal1 | avg_sal2 |
    +--------+----------+----------+
    |     10 |  2916.67 |  2916.67 |
    |     20 |  2175.00 |  2518.75 |
    |     30 |  1566.67 |  1690.00 |
    |     40 |     NULL |     NULL |
    +--------+----------+----------+
    4 rows in set (0.00 sec)
    ```

    ```sql
    mysql> -- 查询至少两门课程及格的学生学号
    mysql> select s_id from sc group by s_id having sum(score>=60)>=2
    ```

30. 

