# MySQL相关面试题

## 1.列举常见的关系型数据库和非关系型都有那些？

**关系型数据库：**

Oracle、DB2、Microsoft SQL Server、Microsoft Access、MySQL

**非关系型数据库：**

NoSql、Cloudant、MongoDb、redis、HBase

**两种数据库之间的区别：**

**关系型数据库**

　　**关系型数据库的特性**

　　1、关系型数据库，是指采用了**关系模型**来组织数据的数据库；

　　2、关系型数据库的最大特点就是**事务的一致性**；

　　3、简单来说，关系模型指的就是**二维表格模型**，而一个关系型数据库就是由二维表及其之间的联系所组成的一个数据组织*。*

　　**关系型数据库的优点**

　　1、**容易理解**：二维表结构是非常贴近逻辑世界一个概念，关系模型相对网状、层次等其他模型来说更容易理解；
　　2、**使用方便**：通用的SQL语言使得操作关系型数据库非常方便；
　　3、**易于维护**：丰富的完整性(实体完整性、参照完整性和用户定义的完整性)大大减低了数据冗余和数据不一致的概率；
　　4、**支持SQL**，可用于复杂的查询。

　　**关系型数据库的缺点**

　　1、为了维护一致性所付出的巨大代价就是其**读写性能比较差**；
　　2、**固定的表结构**；
　　3、**高并发读写需求**；
　　4、**海量数据的高效率读写**；

**非关系型数据库**

　　**非关系型数据库的特性**

　　1、使用**键值对**存储数据；
　　2、**分布式**；
　　3、一般**不支持ACID**特性；
　　4、非关系型数据库严格上不是一种数据库，应该是一种**数据结构化存储**方法的集合。

　　**非关系型数据库的优点**

　　1、无需经过sql层的解析，**读写性能很高**；
　　2、基于键值对，数据没有耦合性，**容易扩展**；
　　3、存储数据的格式：nosql的存储格式是key,value形式、文档形式、图片形式等等，文档形式、图片形式等等，而关系型数据库则只支持基础类型。

　　**非关系型数据库的缺点**

　　 1、**不提供sql支持**，学习和使用成本较高；
　　 2、**无事务处理**，附加功能bi和报表等支持也不好；

## 2.MySQL常见数据库引擎及比较？

主要 MyISAM 与 InnoDB 两个引擎，其主要区别如下：

- InnoDB 支持事务，MyISAM 不支持，这一点是非常之重要。事务是一种高级的处理方式，如在一些列增删改中只要哪个出错还可以回滚还原，而 MyISAM 就不可以了；
- MyISAM 适合查询以及插入为主的应用，InnoDB 适合频繁修改以及涉及到安全性较高的应用；
- InnoDB 支持外键，MyISAM 不支持；
- MyISAM 是默认引擎，InnoDB 需要指定；
- InnoDB 不支持 FULLTEXT 类型的索引；

- InnoDB 中不保存表的行数，如 select count() from table 时，InnoDB；需要扫描一遍整个表来计算有多少行，但是 MyISAM 只要简单的读出保存好的行数即可。注意的是，当 count()语句包含where 条件时 MyISAM 也需要扫描整个表；
- 对于自增长的字段，InnoDB 中必须包含只有该字段的索引，但是在 MyISAM 表中可以和其他字段一起建立联合索引；清空整个表时，InnoDB 是一行一行的删除，效率非常慢。MyISAM 则会重建表；
- InnoDB 支持行锁（某些情况下还是锁整表，如 update table set a=1 where user like '%lee%  

## 3.简述数据三大范式？

- 第一范式（1NF）:原子性 字段不可再分,否则就不是关系数据库;
- 第二范式（2NF）:唯一性 一个表只说明一个事物;
- 第三范式（3NF）:每列都与主键有直接关系，不存在传递依赖;

*PS：第二范式要遵循第一范式，第三范式要遵循第二范式。*



## 4.什么是事务？MySQL如何支持事务？

1. 什么是事务？
   事务由一个或多个sql语句组成一个整体，如果所有的语句执行成功那么修改将会全部生效，如一条sql语句将销量+1，下一条再+1，倘若第二条失败，那么销量将撤销第一条sql语句的+1操作，只有在该事务中所有的语句都执行成功才会将修改加入到数据库中。

2. 事务的特性
   事务具体四大特性，也就是经常说的ACID 

   1. **原子性（Atomicity）** 
        原子性是指事务包含的所有操作要么全部成功，要么全部失败回滚，因此事务的操作如果成功就必须要完全应用到数据库，如果操作失败则不能对数据库有任何影响。 

   2. **一致性（Consistency）** 
        一致性是指事务必须使数据库从一个一致性状态变换到另一个一致性状态，也就是说一个事务执行之前和执行之后都必须处于一致性状态。

        拿转账来说，假设用户A和用户B两者的钱加起来一共是5000，那么不管A和B之间如何转账，转几次账，事务结束后两个用户的钱相加起来应该还得是5000，这就是事务的一致性。

   3. **隔离性（Isolation）** 
      　　隔离性是当多个用户并发访问数据库时，比如操作同一张表时，数据库为每一个用户开启的事务，不能被其他事务的操作所干扰，多个并发事务之间要相互隔离。

         　　即要达到这么一种效果：对于任意两个并发的事务T1和T2，在事务T1看来，T2要么在T1开始之前就已经结束，要么在T1结束之后才开始，这样每个事务都感觉不到有其他事务在并发地执行。

   4. **持久性（Durability）** 
      　　持久性是指一个事务一旦被提交了，那么对数据库中的数据的改变就是永久性的，即便是在数据库系统遇到故障的情况下也不会丢失提交事务的操作。Mysql中会保存有相应的操作日志，即使遭遇故障依然能够通过日志恢复最后一次更新。

      例如我们在使用JDBC操作数据库时，在提交事务方法后，提示用户事务操作完成，当我们程序执行完成直到看到提示后，就可以认定事务以及正确提交，即使这时候数据库出现了问题，也必须要将我们的事务完全执行完成，否则就会造成我们看到提示事务处理完毕，但是数据库因为故障而没有执行事务的重大错误。

## 5. MySql中支持事务的引擎

在MySQL中用的最多的存储引擎有：**innodb，bdb，myisam ,memory** 等。其中innodb和bdb支持事务而myisam等不支持事务。



## 6.简述数据库设计中一对多和多对多的应用场景？

这里可以举一些项目中的例子，就不赘述了

### 7.  如何基于数据库实现商城商品计数器？



常见SQL（必备）
详见武沛齐博客：https://www.cnblogs.com/wupeiqi/articles/5729934.html

### 简述触发器、函数、视图、存储过程
`触发器`:
使用触发器可以定制用户对表进行【增、删、改】操作时前后的行为，注意：没有查询
`存储过程`:
存储过程包含了一系列可执行的sql语句，存储过程存放于MySQL中，通过调用它的名字可以执行其内部的一堆sql

使用存储过程的优点：
1. 用于替代程序写的SQL语句，实现程序与sql解耦
2. 基于网络传输，传别名的数据量小，而直接传sql数据量大
使用存储过程的缺点：
1. 程序员扩展功能不方便

`函数`:
```
一、数学函数
    ROUND(x,y)
        返回参数x的四舍五入的有y位小数的值

    RAND()
        返回０到１内的随机值,可以通过提供一个参数(种子)使RAND()随机数生成器生成一个指定的值。

二、聚合函数(常用于GROUP BY从句的SELECT查询中)
    AVG(col)返回指定列的平均值
    COUNT(col)返回指定列中非NULL值的个数
    MIN(col)返回指定列的最小值
    MAX(col)返回指定列的最大值
    SUM(col)返回指定列的所有值之和
    GROUP_CONCAT(col) 返回由属于一组的列值连接组合而成的结果    

三、字符串函数

    CHAR_LENGTH(str)
        返回值为字符串str 的长度，长度的单位为字符。一个多字节字符算作一个单字符。
    CONCAT(str1,str2,...)
        字符串拼接
        如有任何一个参数为NULL ，则返回值为 NULL。
    CONCAT_WS(separator,str1,str2,...)
        字符串拼接（自定义连接符）
        CONCAT_WS()不会忽略任何空字符串。 (然而会忽略所有的 NULL）。

    CONV(N,from_base,to_base)
        进制转换
        例如：
            SELECT CONV('a',16,2); 表示将 a 由16进制转换为2进制字符串表示

    FORMAT(X,D)
        将数字X 的格式写为'#,###,###.##',以四舍五入的方式保留小数点后 D 位， 并将结果以字符串的形式返回。若  D 为 0, 则返回结果不带有小数点，或不含小数部分。
        例如：
            SELECT FORMAT(12332.1,4); 结果为： '12,332.1000'
    INSERT(str,pos,len,newstr)
        在str的指定位置插入字符串
            pos：要替换位置其实位置
            len：替换的长度
            newstr：新字符串
        特别的：
            如果pos超过原字符串长度，则返回原字符串
            如果len超过原字符串长度，则由新字符串完全替换
    INSTR(str,substr)
        返回字符串 str 中子字符串的第一个出现位置。

    LEFT(str,len)
        返回字符串str 从开始的len位置的子序列字符。

    LOWER(str)
        变小写

    UPPER(str)
        变大写

    REVERSE(str)
        返回字符串 str ，顺序和字符顺序相反。

    SUBSTRING(str,pos) , SUBSTRING(str FROM pos) SUBSTRING(str,pos,len) , SUBSTRING(str FROM pos FOR len)
        不带有len 参数的格式从字符串str返回一个子字符串，起始于位置 pos。带有len参数的格式从字符串str返回一个长度同len字符相同的子字符串，起始于位置 pos。 使用 FROM的格式为标准 SQL 语法。也可能对pos使用一个负值。假若这样，则子字符串的位置起始于字符串结尾的pos 字符，而不是字符串的开头位置。在以下格式的函数中可以对pos 使用一个负值。

        mysql> SELECT SUBSTRING('Quadratically',5);
            -> 'ratically'

        mysql> SELECT SUBSTRING('foobarbar' FROM 4);
            -> 'barbar'

        mysql> SELECT SUBSTRING('Quadratically',5,6);
            -> 'ratica'

        mysql> SELECT SUBSTRING('Sakila', -3);
            -> 'ila'

        mysql> SELECT SUBSTRING('Sakila', -5, 3);
            -> 'aki'

        mysql> SELECT SUBSTRING('Sakila' FROM -4 FOR 2);
            -> 'ki'

四、日期和时间函数
    CURDATE()或CURRENT_DATE() 返回当前的日期
    CURTIME()或CURRENT_TIME() 返回当前的时间
    DAYOFWEEK(date)   返回date所代表的一星期中的第几天(1~7)
    DAYOFMONTH(date)  返回date是一个月的第几天(1~31)
    DAYOFYEAR(date)   返回date是一年的第几天(1~366)
    DAYNAME(date)   返回date的星期名，如：SELECT DAYNAME(CURRENT_DATE);
    FROM_UNIXTIME(ts,fmt)  根据指定的fmt格式，格式化UNIX时间戳ts
    HOUR(time)   返回time的小时值(0~23)
    MINUTE(time)   返回time的分钟值(0~59)
    MONTH(date)   返回date的月份值(1~12)
    MONTHNAME(date)   返回date的月份名，如：SELECT MONTHNAME(CURRENT_DATE);
    NOW()    返回当前的日期和时间
    QUARTER(date)   返回date在一年中的季度(1~4)，如SELECT QUARTER(CURRENT_DATE);
    WEEK(date)   返回日期date为一年中第几周(0~53)
    YEAR(date)   返回日期date的年份(1000~9999)

    重点:
    DATE_FORMAT(date,format) 根据format字符串格式化date值

       mysql> SELECT DATE_FORMAT('2009-10-04 22:23:00', '%W %M %Y');
        -> 'Sunday October 2009'
       mysql> SELECT DATE_FORMAT('2007-10-04 22:23:00', '%H:%i:%s');
        -> '22:23:00'
       mysql> SELECT DATE_FORMAT('1900-10-04 22:23:00',
        ->                 '%D %y %a %d %m %b %j');
        -> '4th 00 Thu 04 10 Oct 277'
       mysql> SELECT DATE_FORMAT('1997-10-04 22:23:00',
        ->                 '%H %k %I %r %T %S %w');
        -> '22 22 10 10:23:00 PM 22:23:00 00 6'
       mysql> SELECT DATE_FORMAT('1999-01-01', '%X %V');
        -> '1998 52'
       mysql> SELECT DATE_FORMAT('2006-06-00', '%d');
        -> '00'

五、加密函数
    MD5()    
        计算字符串str的MD5校验和
    PASSWORD(str)   
        返回字符串str的加密版本，这个加密过程是不可逆转的，和UNIX密码加密过程使用不同的算法。

六、控制流函数            
    CASE WHEN[test1] THEN [result1]...ELSE [default] END
        如果testN是真，则返回resultN，否则返回default
    CASE [test] WHEN[val1] THEN [result]...ELSE [default]END  
        如果test和valN相等，则返回resultN，否则返回default

    IF(test,t,f)   
        如果test是真，返回t；否则返回f

    IFNULL(arg1,arg2) 
        如果arg1不是空，返回arg1，否则返回arg2

    NULLIF(arg1,arg2) 
        如果arg1=arg2返回NULL；否则返回arg1        

```
`视图`:
视图是一个虚拟表（非真实存在），其本质是【根据SQL语句获取动态的数据集，并为其命名】，用户使用时只需使用【名称】即可获取结果集，可以将该结果集当做表来使用。

使用视图我们可以把查询过程中的临时表摘出来，用视图去实现，这样以后再想操作该临时表的数据时就无需重写复杂的sql了，直接去视图中查找即可，但视图有明显地效率问题，并且视图是存放在数据库中的，如果我们程序中使用的sql过分依赖数据库中的视图，即强耦合，那就意味着扩展sql极为不便，因此并不推荐使用

---


### MySQL索引种类
MySQL目前主要有以下几种索引类型：
1. 普通索引
2. 唯一索引
3. 主键索引
4. 组合索引
5. 全文索引

[mysql索引类型](https://www.jianshu.com/p/7a0c215edb1d)
------------

### 索引在什么情况下遵循最左前缀的规则？
最左前缀匹配原则
在mysql建立联合索引时会遵循最左前缀匹配的原则，即最左优先，在检索数据时从联合索引的最左边开始匹配

示例：
```
CREATE TABLE `user` (
  `id` int(10) unsigned NOT NULL AUTO_INCREMENT,
  `name` char(32) NOT NULL,
  `city` varchar(30) NOT NULL,
  `age` tinyint(4) NOT NULL,
  PRIMARY KEY (`id`),
  KEY `name_city_name` (`name`,`city`,`age`)
) ENGINE=InnoDB AUTO_INCREMENT=6103 DEFAULT CHARSET=utf8;
```
联合索引

``` 
KEY "name_city_name" ("name","city","age") 
```
实际上建立了 (name),(name,city),(name,city,age) 三个索引

-------

### 主键和外键的区别？
定义：
主键：唯一标识一条记录，不能有重复，不允许为空。
外键：表的外键是另一表的主键，外键是可以有重复的，可以是空值。
索引：该字段没有重复值，但可以有一个空值。

作用：
主键：用来保证数据完整性
外键：用来和其他表建立联系用
索引：用来提高查询排序的速度

个数：
主键：主键只能有一个。
外键：一个表可以有多个外键。
索引：一个表可以有多个唯一索引。

------

### MySQL常见的函数？
```
一、数学函数
    ROUND(x,y)
        返回参数x的四舍五入的有y位小数的值

    RAND()
        返回０到１内的随机值,可以通过提供一个参数(种子)使RAND()随机数生成器生成一个指定的值。

二、聚合函数(常用于GROUP BY从句的SELECT查询中)
    AVG(col)返回指定列的平均值
    COUNT(col)返回指定列中非NULL值的个数
    MIN(col)返回指定列的最小值
    MAX(col)返回指定列的最大值
    SUM(col)返回指定列的所有值之和
    GROUP_CONCAT(col) 返回由属于一组的列值连接组合而成的结果    

三、字符串函数

    CHAR_LENGTH(str)
        返回值为字符串str 的长度，长度的单位为字符。一个多字节字符算作一个单字符。
    CONCAT(str1,str2,...)
        字符串拼接
        如有任何一个参数为NULL ，则返回值为 NULL。
    CONCAT_WS(separator,str1,str2,...)
        字符串拼接（自定义连接符）
        CONCAT_WS()不会忽略任何空字符串。 (然而会忽略所有的 NULL）。

    CONV(N,from_base,to_base)
        进制转换
        例如：
            SELECT CONV('a',16,2); 表示将 a 由16进制转换为2进制字符串表示

    FORMAT(X,D)
        将数字X 的格式写为'#,###,###.##',以四舍五入的方式保留小数点后 D 位， 并将结果以字符串的形式返回。若  D 为 0, 则返回结果不带有小数点，或不含小数部分。
        例如：
            SELECT FORMAT(12332.1,4); 结果为： '12,332.1000'
    INSERT(str,pos,len,newstr)
        在str的指定位置插入字符串
            pos：要替换位置其实位置
            len：替换的长度
            newstr：新字符串
        特别的：
            如果pos超过原字符串长度，则返回原字符串
            如果len超过原字符串长度，则由新字符串完全替换
    INSTR(str,substr)
        返回字符串 str 中子字符串的第一个出现位置。

    LEFT(str,len)
        返回字符串str 从开始的len位置的子序列字符。

    LOWER(str)
        变小写

    UPPER(str)
        变大写

    REVERSE(str)
        返回字符串 str ，顺序和字符顺序相反。

    SUBSTRING(str,pos) , SUBSTRING(str FROM pos) SUBSTRING(str,pos,len) , SUBSTRING(str FROM pos FOR len)
        不带有len 参数的格式从字符串str返回一个子字符串，起始于位置 pos。带有len参数的格式从字符串str返回一个长度同len字符相同的子字符串，起始于位置 pos。 使用 FROM的格式为标准 SQL 语法。也可能对pos使用一个负值。假若这样，则子字符串的位置起始于字符串结尾的pos 字符，而不是字符串的开头位置。在以下格式的函数中可以对pos 使用一个负值。

        mysql> SELECT SUBSTRING('Quadratically',5);
            -> 'ratically'

        mysql> SELECT SUBSTRING('foobarbar' FROM 4);
            -> 'barbar'

        mysql> SELECT SUBSTRING('Quadratically',5,6);
            -> 'ratica'

        mysql> SELECT SUBSTRING('Sakila', -3);
            -> 'ila'

        mysql> SELECT SUBSTRING('Sakila', -5, 3);
            -> 'aki'

        mysql> SELECT SUBSTRING('Sakila' FROM -4 FOR 2);
            -> 'ki'

四、日期和时间函数
    CURDATE()或CURRENT_DATE() 返回当前的日期
    CURTIME()或CURRENT_TIME() 返回当前的时间
    DAYOFWEEK(date)   返回date所代表的一星期中的第几天(1~7)
    DAYOFMONTH(date)  返回date是一个月的第几天(1~31)
    DAYOFYEAR(date)   返回date是一年的第几天(1~366)
    DAYNAME(date)   返回date的星期名，如：SELECT DAYNAME(CURRENT_DATE);
    FROM_UNIXTIME(ts,fmt)  根据指定的fmt格式，格式化UNIX时间戳ts
    HOUR(time)   返回time的小时值(0~23)
    MINUTE(time)   返回time的分钟值(0~59)
    MONTH(date)   返回date的月份值(1~12)
    MONTHNAME(date)   返回date的月份名，如：SELECT MONTHNAME(CURRENT_DATE);
    NOW()    返回当前的日期和时间
    QUARTER(date)   返回date在一年中的季度(1~4)，如SELECT QUARTER(CURRENT_DATE);
    WEEK(date)   返回日期date为一年中第几周(0~53)
    YEAR(date)   返回日期date的年份(1000~9999)

    重点:
    DATE_FORMAT(date,format) 根据format字符串格式化date值

       mysql> SELECT DATE_FORMAT('2009-10-04 22:23:00', '%W %M %Y');
        -> 'Sunday October 2009'
       mysql> SELECT DATE_FORMAT('2007-10-04 22:23:00', '%H:%i:%s');
        -> '22:23:00'
       mysql> SELECT DATE_FORMAT('1900-10-04 22:23:00',
        ->                 '%D %y %a %d %m %b %j');
        -> '4th 00 Thu 04 10 Oct 277'
       mysql> SELECT DATE_FORMAT('1997-10-04 22:23:00',
        ->                 '%H %k %I %r %T %S %w');
        -> '22 22 10 10:23:00 PM 22:23:00 00 6'
       mysql> SELECT DATE_FORMAT('1999-01-01', '%X %V');
        -> '1998 52'
       mysql> SELECT DATE_FORMAT('2006-06-00', '%d');
        -> '00'

五、加密函数
    MD5()    
        计算字符串str的MD5校验和
    PASSWORD(str)   
        返回字符串str的加密版本，这个加密过程是不可逆转的，和UNIX密码加密过程使用不同的算法。

六、控制流函数            
    CASE WHEN[test1] THEN [result1]...ELSE [default] END
        如果testN是真，则返回resultN，否则返回default
    CASE [test] WHEN[val1] THEN [result]...ELSE [default]END  
        如果test和valN相等，则返回resultN，否则返回default

    IF(test,t,f)   
        如果test是真，返回t；否则返回f

    IFNULL(arg1,arg2) 
        如果arg1不是空，返回arg1，否则返回arg2

    NULLIF(arg1,arg2) 
        如果arg1=arg2返回NULL；否则返回arg1        

```

### 列举 创建索引但是无法命中索引的8种情况。
1. 应尽量避免在 where 子句中使用 != 或 <> 操作符，否则引擎将放弃使用索引而进行全表扫描；
2. 尽量避免在 where 子句中使用 or 来连接条件，否则将导致引擎放弃使用索引而进行全表扫描，即使其中有条件带索引也不会使用，这也是为什么尽量少用 or 的原因；



3. 对于多列索引，不是使用的第一部分，则不会使用索引；

4. 如果列类型是字符串，那一定要在条件中将数据使用引号引用起来，否则不会使用索引；

5. like的模糊查询以 % 开头，索引失效；



6. 应尽量避免在 where 子句中对字段进行表达式操作，这将导致引擎放弃使用索引而进行全表扫描；

如：

```
select id from t where num/2 = 100 
```

应改为:

```
select id from t where num = 100*2；
```

7、应尽量避免在 where 子句中对字段进行函数操作，这将导致引擎放弃使用索引而进行全表扫描；

例如：
```
select id from t where substring(name,1,3) = 'abc' – name;
```
以abc开头的，应改成：
```
select id from t where name like 'abc%' 
```
例如：
```
select id from t where datediff(day, createdate, '2005-11-30') = 0 – '2005-11-30';
```
应改为:
```
select id from t where createdate >= '2005-11-30' and createdate < '2005-12-1';
```
8. 不要在 where 子句中的 “=” 左边进行函数、算术运算或其他表达式运算，否则系统将可能无法正确使用索引；
9. 如果MySQL估计使用全表扫描要比使用索引快，则不使用索引；
10. 不适合键值较少的列（重复数据较多的列）
假如索引列TYPE有5个键值，如果有1万条数据，那么 WHERE TYPE = 1将访问表中的2000个数据块。再加上访问索引块，一共要访问大于200个的数据块。如果全表扫描，假设10条数据一个数据块，那么只需访问1000个数据块，既然全表扫描访问的数据块少一些，肯定就不会利用索引了。



1、应尽量避免在 where 子句中使用 != 或 <> 操作符，否则引擎将放弃使用索引而进行全表扫描；



2、尽量避免在 where 子句中使用 or 来连接条件，否则将导致引擎放弃使用索引而进行全表扫描，即使其中有条件带索引也不会使用，这也是为什么尽量少用 or 的原因；



3、对于多列索引，不是使用的第一部分，则不会使用索引；

4、如果列类型是字符串，那一定要在条件中将数据使用引号引用起来，否则不会使用索引；



5、like的模糊查询以 % 开头，索引失效；



6、应尽量避免在 where 子句中对字段进行表达式操作，这将导致引擎放弃使用索引而进行全表扫描；

如：
```
select id from t where num/2 = 100 
```
应改为:
```
select id from t where num = 100*2；
```
7、应尽量避免在 where 子句中对字段进行函数操作，这将导致引擎放弃使用索引而进行全表扫描；

例如：
```
select id from t where substring(name,1,3) = 'abc' – name;
```
以abc开头的，应改成：
```
select id from t where name like ‘abc%’ 
```
例如：
```
select id from t where datediff(day, createdate, '2005-11-30') = 0 – '2005-11-30';
```
应改为:
```
select id from t where createdate >= '2005-11-30' and createdate < '2005-12-1';
```
8、不要在 where 子句中的 “=” 左边进行函数、算术运算或其他表达式运算，否则系统将可能无法正确使用索引；

9、如果MySQL估计使用全表扫描要比使用索引快，则不使用索引；

10、不适合键值较少的列（重复数据较多的列）

假如索引列TYPE有5个键值，如果有1万条数据，那么 WHERE TYPE = 1将访问表中的2000个数据块。再加上访问索引块，一共要访问大于200个的数据块。如果全表扫描，假设10条数据一个数据块，那么只需访问1000个数据块，既然全表扫描访问的数据块少一些，肯定就不会利用索引了。

---------------------
> 作者：徐刘根 
> 来源：CSDN 
> 原文：https://blog.csdn.net/xlgen157387/article/details/79572598 
> 版权声明：本文为博主原创文章，转载请附上博文链接！
---------------------





如何开启慢日志查询？

数据库导入导出命令（结构+数据）？

### 数据库优化方案？

1. 优化索引、SQL 语句、分析慢查询；
2. 设计表的时候严格根据数据库的设计范式来设计数据库；
3. 使用缓存，把经常访问到的数据而且不需要经常变化的数据放在缓存中，能节约磁盘 IO
4. 优化硬件；采用 SSD，使用磁盘队列技术(RAID0,RAID1,RDID5)等
5. 采用 MySQL 内部自带的表分区技术，把数据分层不同的文件，能够提高磁盘的读取效率；
6. 垂直分表；把一些不经常读的数据放在一张表里，节约磁盘 I/O；
7. 主从分离读写；采用主从复制把数据库的读操作和写入操作分离开来；
8. 分库分表分机器（数据量特别大），主要的的原理就是数据路由；
9. 选择合适的表引擎，参数上的优化
10. 进行架构级别的缓存，静态化和分布式；
11. 不采用全文索引；
12. 采用更快的存储方式，例如 NoSQL 存储经常访问的数据**。 

### char和varchar的区别？

简述MySQL的执行计划？

### 在对name做了唯一索引前提下，简述以下区别：

``````mysql
select * from tb where name = ‘Oldboy-Wupeiqi’
select * from tb where name = ‘Oldboy-Wupeiqi’ limit 1
``````

第二条SQL语句限制了输出的行数，只显示一条

### 1000w条数据，使用limit offset 分页时，为什么越往后翻越慢？如何解决？



什么是索引合并？

什么是覆盖索引？

简述数据库读写分离？

简述数据库分库分表？（水平、垂直）
