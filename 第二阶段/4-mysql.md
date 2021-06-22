# 1、初识MySQL

JavaEE：企业级Java开发 Web

前端（页面：展示：数据）

后台 （连接点：连接数据库JDBC,连接前端（控制视图跳转，给前端传递数据））

数据库（存数据，Txt,Excel,Word）

```txt
只会写代码，学好数据库，基本混饭吃：

操作系统，数据结构与算法！当一个不错的程序猿！

离散数学，数字电路，体系结构，编译原理。+实战经验，优秀程序猿
```

### 1.1为什么学数据库

1、岗位需求

2、现在的世界，大数据时代，得数据者得天下

3、被迫需求：存数据

**`4、数据库是所有软件体系中最核心的存在` DBA**

### 1.2 什么是数据库

数据库：(DB,DataBase)

概念:数据仓库，软件，安装在操作系统之（windows,Linux。mac）上的！SQL,可以存储大量的数据，500万!

作用:存储数据，管理数据 Excel

### 1.3 数据库分类

关系型数据库：(SQL)

- MySQL, Oracle, sql Server, DB2, SQLite
- 通过表和表之间，行和列之间的关系进行数据的存储

非关系型数据库：(NoSQL) Not Only SQL

- Redis, MongDB
- 非关系型数据库，对象存储，通过对象自身的属性来决定

**DBMS(数据库管理系统) **

- 数据库的管理软件，科学有效的管理我们的数据，维护和获取
- MySQL ，数据管理系统！

### 1.4 MySQL简介

MySQL是一个**[关系型数据库管理系统](https://baike.baidu.com/item/关系型数据库管理系统/696511)**

前世： 瑞典MySQL AB 公司

今身： 属于 [Oracle](https://baike.baidu.com/item/Oracle) 旗下产品

MySQL是最好的 [RDBMS](https://baike.baidu.com/item/RDBMS/1048260) (Relational Database Management System，关系数据库管理系统) 应用软件之一。

开源的数据库软件

体积小，速度快，总体拥有成本低，招人成本比较低。

中小型网站，或者大型网站，集群

官网： https://www.mysql.com/

### 1.5连接数据库

命令行连接

```sql
mysql -uroot -pzhou --连接数据库

update mysql.user set authentication_string=password('123456') where user='root' and Host='localhost';  --修改密码

flush privileges;--刷新权限
--------------------------------------------------
--所有语句使用;结尾--

show databases;--查看所有的数据库

mysql> use school--切换数据库， use 数据库名
Database changed

--

show tables;--查看数据库中所有的表
describe student;--显示数据库中所有的表的信息
create database westos;--创建一个数据库

exit;--退出连接

--单行注释（sql本来注释）
/*
多行注释
*/

```

# 2、操作数据库

操作数据库》操作数据库中的表》操作数据库中表的数据

**MySQL不区分大小写**

### 2.1操作数据库

1.创建数据库

```sql
CREATE DATABASE IF NOT EXISTS westos;
```

2.删除数据库

```sql
DROP DATABASE IF EXISTS westos
```

3.使用数据库

```sql
-- ``,如果你的表名或者字段名是一个特殊字符，需要带``

USE 'school'
```

4.查看数据库

```mysql
SHOW DATABASES--查看所有数据库
```

### 2.2数据库的列类型

**数值**

tinyint 十分小的数据 1个字节
smallint 较小的数据 2个字节
mediumint 中等大小 3个字节
int 标准的整数 4个字节（常用）
bigint 较大的数据 8个字节
float 浮点数 4个字节
double 浮点数 8个字节 （精度问题）
decimal 字符串形式的浮点数,金融计算的时候，一般用

**字符串**

- char 字符串固定大小 0-255
- **varchar 可变字符串 0-65535**（常用）
- tinytext 微型文本 2^8-1
- **text 文本串 2^16-1** (保存大文本)

**时间日期**

java.util.Date

- date YYYY-MM-DD，日期
- time HH:mm:ss 时间格式
- **datetime YYYY-MM-DD HH:mm:ss 最常用的时间格式**
- timestamp 时间戳 1970.1.1到现在的毫秒数
- year 年份表示

**null**

- 没有值，未知
- **注意，不要使用null进行运算**，结果为null

### 2.3数据库的字段类型（重点）

unsigened:

- 无符号的整数
- 声明该列不能声明负数

zerofill:

- 0填充的
- 10的长度 1 – 0000000001 不足位数用0 填充

自增：

- 通常理解为自增，自动在上一条记录的基础上+1
- 通常用来设计唯一的主键 index,必须是整数类似
- 可以自定义设置主键自增的起始值和步长

非空 NULL not Null

- 假设设置为 not null，如何不给他赋值，就会报错
- NULL 如果不填写，默认为NULL

默认：

- 设置默认的值！

### 2.4 创建数据库表

格式:

```mysql
CREATE TABLE [IF NOT EXISTS] `表名`（
`字段名` 列类型[属性][索引][注释],
`字段名` 列类型[属性][索引][注释],
...
`字段名` 列类型[属性][索引][注释]
）[表类型][表的字符集设置][注释]

```



```mysql
--目标:创建一个schoo1数据库

--创建学生表(列,字段)使用SQL 创建

--学号int 登录密码varchar(20)姓名,性别varchar(2),出生日期(datatime)，家庭住址，emai1--注意点，使用英文()，表的名称和字段尽量使用括起来

-- AUTO_ INCREMENT 自增

--字符串使用单引号括起来!

--所有的语句后面加，(英文的)，最后一个不用加

-- PRIMARY KEY 主键，一般- 一个表只有一个唯一 -的主键!
CREATE DATABASE school
CREATE TABLE IF NOT EXISTS `student` (
`id` INT(4) NOT NULL AUTO_INCREMENT COMMENT '学号',
`name` VARCHAR(30) NOT NULL DEFAULT '匿名' COMMENT '姓名',
`pwd` VARCHAR(20) NOT NULL DEFAULT '123456' COMMENT '密码',
`sex` VARCHAR(2) NOT NULL DEFAULT '男' COMMENT '性别',
`birthday` DATETIME DEFAULT NULL COMMENT '出生日期',
`address` VARCHAR(100) DEFAULT NULL COMMENT '家庭住址',
`email` VARCHAR(50) DEFAULT NULL COMMENT '邮箱',
PRIMARY KEY (`id`)
)ENGINE=INNODB DEFAULT CHARSET=utf8

```

常用命令

```mysql
SHOW CREATE DATABASE school -- 查看创建数据库的语句
SHOW CREATE TABLE student -- 查看student数据表的定义语句
DESC student -- 显示表的结构

```

### 2.5数据表的类型

```mysql
-- 关于数据库引擎
/*
INNODB 默认使用
MYISAM 早些年使用
*/

```

|              | MYISAM | INNODB                 |
| ------------ | ------ | ---------------------- |
| 事务支持     | 不支持 | 支持                   |
| 数据行锁定   | 不支持 | 支持                   |
| 外键约束     | 不支持 | 支持                   |
| 全文索引     | 支持   | 不支持                 |
| 表空间的大小 | 较小   | 较大，约为MYISAM的两倍 |

常规使用操作：

- MYISAM 节约空间，速度较快，
- INNODB 安全性高，事务处理，多表多用户操作

在物理空间存在的位置

所有的数据库文件都存在data目录下，一个文件夹就对应一个数据库

本质还是文件的存储

MySQL 引擎在物理文件上的区别

- innoDB 在数据库表中，只有一个*.frm文件，以及上级目录下的ibdata1文件
- MYISAM 对应的文件
  - *.frm - 表结构的定义文件
  - *. MYD -数据文件
  - *.MYI 索引文件

设置数据库字符集编码

```sql
CHARTSET=UTF8
```

不设置的话，会是mysql默认的字符集编码-（不支持中文）

可以在my.ini中配置默认的编码

```sql
character-set-server=utf8

```

### 2.6修改删除表

```	sql
-- 修改表名 ALTER TABLE 旧表面 AS 新表名
ALTER TABLE student RENAME  AS student1
-- 增加表的字段 ALTER TABLE 表名 ADD 字段名 列属性
ALTER TABLE student1 ADD age INT(11)
-- 修改表的字段（重命名，修改约束）
ALTER TABLE student1 MODIFY age VARCHAR(11)  -- 修改约束
ALTER TABLE student1 CHANGE age age1 INT(1)  -- 字段重命名

-- 删除表的字段
ALTER TABLE student1 DROP age1

-- 删除表
DROP TABLE IF EXISTS student1

所有的创建和删除操作尽量加上判断，以免报错
```

注意点：

- `` 字段名，使用这个包裹
- 注释 – /**/
- sql 关键字大小写不敏感，建议写小写
- 所有的符号全部用英文

# 3、MySQL数据管理

### 3.1外键（了解）

方式一：在创建表的时候，增加约束（麻烦，比较复杂）

```sql
CREATE TABLE `grade`(
`gradeid` INT(10) NOT NULL AUTO_INCREMENT COMMENT '年级id',
`gradename` VARCHAR(50) NOT NULL COMMENT '年级名称',
PRIMARY KEY (`gradeid`)
)ENGINE=INNODB DEFAULT CHARSET=utf8

-- 学生表的 gradeid 字段 要去引用年级表的gradeid
-- 定义外键KEY
-- 给这个外键添加约束（执行引用） references 引用
CREATE TABLE IF NOT EXISTS `student` (
`id` INT(4) NOT NULL AUTO_INCREMENT COMMENT '学号',
`name` VARCHAR(30) NOT NULL DEFAULT '匿名' COMMENT '姓名',
`pwd` VARCHAR(20) NOT NULL DEFAULT '123456' COMMENT '密码',
`sex` VARCHAR(2) NOT NULL DEFAULT '男' COMMENT '性别',
`birthday` DATETIME DEFAULT NULL COMMENT '出生日期',
`gradeid` INT(10) NOT NULL COMMENT '学生年级',
`address` VARCHAR(100) DEFAULT NULL COMMENT '家庭住址',
`email` VARCHAR(50) DEFAULT NULL COMMENT '邮箱',
PRIMARY KEY (`id`),
KEY `FK_gardeid` (`gradeid`),
CONSTRAINT `FK_gardeid` FOREIGN KEY (`gradeid`) REFERENCES `grade` (gradeid)
)ENGINE=INNODB DEFAULT CHARSET=utf8

```

删除有外键关系的表的时候，必须先删除引用的表（从表），再删除被引用的表（主表）

方式二： 创建表成功后添加外键

```sql
CREATE TABLE `grade`(
`gradeid` INT(10) NOT NULL AUTO_INCREMENT COMMENT '年级id',
`gradename` VARCHAR(50) NOT NULL COMMENT '年级名称',
PRIMARY KEY (`gradeid`)
)ENGINE=INNODB DEFAULT CHARSET=utf8

-- 学生表的 gradeid 字段 要去引用年级表的gradeid
-- 定义外键KEY
-- 给这个外键添加约束（执行引用） references 引用
CREATE TABLE IF NOT EXISTS `student` (
`id` INT(4) NOT NULL AUTO_INCREMENT COMMENT '学号',
`name` VARCHAR(30) NOT NULL DEFAULT '匿名' COMMENT '姓名',
`pwd` VARCHAR(20) NOT NULL DEFAULT '123456' COMMENT '密码',
`sex` VARCHAR(2) NOT NULL DEFAULT '男' COMMENT '性别',
`birthday` DATETIME DEFAULT NULL COMMENT '出生日期',
`gradeid` INT(10) NOT NULL COMMENT '学生年级',
`address` VARCHAR(100) DEFAULT NULL COMMENT '家庭住址',
`email` VARCHAR(50) DEFAULT NULL COMMENT '邮箱',
PRIMARY KEY (`id`)

)ENGINE=INNODB DEFAULT CHARSET=utf8

-- 创建表的时候没有外键关系
ALTER TABLE `student`
ADD CONSTRAINT `FK_gradeid` FOREIGN KEY (`gradeid`) REFERENCES `grade`(`gradeid`);

-- ALTER TABLE`表`  ADD CONSTRAINT 约束名 FOREIGN KEY（作为外键的列） 引用到哪个表的哪个字段

```

以上的操作都是物理外键，数据库级别外键，不建议使用。（避免数据库过多造成困扰）

**最佳实践**

- 数据库就是单纯的表，只用来存数据，只有行（数据）和列（字段）
- 我们想使用多张表的数据，想使用外键（程序去实现）

### 3.2 DML语言（全记住）

数据库意义：数据存储，数据管理

DML语言：数据操作语言

- Insert
- update
- delete

### 3.3添加

> insert

```sql
-- 插入语句（添加）
-- nsert into 表名（[字段一], [字段二]）values('值1'),('值2')

INSERT INTO `grade` (`gradename`) VALUES('大四')

-- 由于主键自增我们可以省略（如何不写表的字段，他会一一匹配）
INSERT INTO `grade` VALUES('大三')
INSERT INTO `grade` (`gradeid`,`gradename`) VALUES ('大三','null')

-- 一般写插入语句，我们一定要数据和字段一一对应。
-- 插入多个字段
INSERT INTO `grade`(`gradename`) VALUES ('大二'),('大一');


INSERT INTO `student`(`name`) VALUES ('张三')

INSERT INTO `student`(`name`,`pwd`,`sex`) VALUES ('张三','aaaaa','男')
INSERT INTO `student`(`name`,`pwd`,`sex`) 
VALUES ('李四','aaaaa','男'),('王五','23232','女')


```

语法：-- insert into 表名（[字段一], [字段二]）values(‘值1’),(‘值2’)

注意事项：

1.字段和字段之间用逗号分开

2.字段可以省略，但是后面的值必须一一对应

3.可以同时插入多条数据，VALUES后面的值需要使用，隔开即可

```sql
INSERT INTO `student`(`name`,`pwd`,`sex`) 
VALUES ('李四','aaaaa','男'),('王五','23232','女')


```

### 3.4 修改

update 修改谁（条件） set 原来的值=新值

```sql

-- 修改学员名字

UPDATE `student` SET `name`='囷' WHERE id =1;
-- 不指定条件的情况下，会改动所有表
UPDATE `student` SET `name`='233'

-- 语法；
-- UPDATE 表名 set column_name,[] = value where 条件


```

条件：where 子句 运算符 id 等于 某个值，大于某个值，在某个区间内修改

操作符返回布尔值

| 操作符      | 含义                   | 范围      | 结果  |
| ----------- | ---------------------- | --------- | ----- |
| =           | 等于                   | 5=6       | false |
| != <>       | 不等于                 | 5！=6     | true  |
| >           | 大于                   |           |       |
| <           | 小于                   |           |       |
| >=          |                        |           |       |
| <=          |                        |           |       |
| between and | 在某个范围内，闭合区间 |           |       |
| and         | &&                     | 5>1and1>2 | false |
| or          | \|\|                   | 5>1or1>2  | true  |

注意：

- column_name 是数据库的列，带上``
- 条件，是筛选的条件，如果没有指定，则会修改所有的列
- value 是一个具体的值，也可以是一个变量
- 多个设置的属性之间，使用英文逗号隔开

```sql
UPDATE `student` SET `birthday`=CURRENT_TIME where `name`='李四' AND SEX = '男'


```

### 3.5 删除

> delete 命令

语法 `delete from 表名 [where 条件]`

```sql
-- 删除数据 (避免这样写)
DELETE FROM `student`

-- 删除指定
DELETE FROM `student` where id= 1


```

TRUNCATE 命令

作用：完全清空一个数据库，表的结构和索引不会变

> delete 和 TRUNCATE 区别

- 相同点： 都能删除数据，都不会删除表结构
- 不同：
  - TRUNCATE 重新设置自增列 计数器会归零
  - TRUNCATE 不会影响事务

```sql
-- 测试delete 和 truncate 区别

CREATE TABLE `test`(
`id` INT(4) NOT NULL AUTO_INCREMENT,
`coll` VARCHAR(20) NOT NULL,
PRIMARY KEY (`id`)
)ENGINE=INNODB DEFAULT CHARSET=utf8

INSERT INTO `test`(`coll`) VALUES('1'),('2'),('3')

DELETE FROM `test` -- 不会影响自增

TRUNCATE TABLE `test` -- 自增会归零


```

了解即可：`delete删除的问题` 重启数据库，现象

- innoDB 自增列会从1开始（存在内存当中，断电即失）
- MyISAM 继续从上一个自增量开始（存在文件中，不会丢失）

# 4、DQL查询数据（最重点）

### 4.1DQL

(Data Query Language) :数据查询语言

- 所有的查询操作都用它 Select
- 简单的查询，复杂的查询它都能做
- **数据库中最核心的语言**
- 使用频率最高的语言

### 4.2指定查询字段

```sql
-- 查询  SELECT 字段 FROM 表

-- 查询指定字段  such as
SELECT `StudentNo`,`StudentName` FROM student

-- 别名，给结果起一个名字 AS   可以给字段起别名 也可以给表起别名
SELECT `StudentNo` AS 学号,`StudentName`AS 学生姓名 FROM student AS S

-- 函数 Concat(a,b)
SELECT CONCAT('姓名：',StudentName) AS 新名字 FROM student


```

语法： `SELECT 字段 ... FROM 表`

> 有时候，列名字不是那么见名知意。我们起别名 AS 字段名 AS 别名 表名 AS 别名

**去重**

作用：去除select语句查询出来的结果中重复的语句，重复的语句只显示一条

```sql
-- 查询一下有哪些同学参加了考试，成绩
SELECT * FROM result -- 查询全部的考试成绩
-- 查询有哪些同学参加了考试
SELECT `studentNo` FROM result 
-- 发现重复数据，去重
SELECT DISTINCT `studentNo` FROM result 


```

数据库的列（表达式）

```sql
SELECT VERSION()  --查询系统版本（函数）
SELECT 100*3-1 AS 计算结果 -- 用来计算（表达式）
SELECT @@auto_increment_increment --查询自增的步长（变量）

-- 学员考试成绩+1 分 查看
SELECT `StudentNo`,`StudentResult`+1 AS '提分后' FROM result



```

数据库中的表达式： 文本值，列，Null , 函数，计算表达式，系统变量…

select `表达式` from 表

### 4.3where 条件子句

作用：检索数据中符合条件的值

> 逻辑运算符

| 运算符  | 语法          | 结果   |
| ------- | ------------- | ------ |
| and &&  | a and b a&&b  | 逻辑与 |
| or \|\| | a or b a\|\|b | 逻辑或 |
| Not !=  | not a !a      | 逻辑非 |

**尽量使用英文**

```sql
-- 查询考试成绩在95分到100分之间
SELECT `StduentNo`,`StudentResult` FROM result
WHERE StudentResult >=95 AND StudentResult<=100

-- 模糊查询（区间）
SELECT `StduentNo`,`StudentResult` FROM result
WHERE StudentResult BETWEEN 95 AND 100

-- 除了1000号学生之外的同学成绩
SELECT `StduentNo`,`StudentResult` FROM result
WHERE NOT StudentNo = 1000

```

模糊查询：比较运算符

运算符											语法									描述
I S NULL									a is null									如果操作符为null 结果为真
IS NOT NULL							a is not null							如果操作符为not null 结果为真
BETWEEN								a between b and c					若a在b 和c之间则为真
LIKE											a like b									SQL匹配，如果a 匹配到b 则为真
IN												a in (a1,a2,a3…)						假设a 在 a1,a2,a3其中的某一个中，为真

```sql
--  查询姓刘的同学
-- like结合 %（代表0到任意字符）  _(一个字符)
SELECT `StudentNo`,`StudentName` FROM `student`
WHERE StudentName LIKE '刘%';

-- 查询姓刘的同学，名字后只有一个字
SELECT `StudentNo`,`StudentName` FROM `student`
WHERE StudentName LIKE '刘_';

-- 查询姓刘的同学，名字后只有两个字
SELECT `StudentNo`,`StudentName` FROM `student`
WHERE StudentName LIKE '刘__';

-- 查询名字中间有嘉字的同学 %嘉%
SELECT `StudentNo`,`StudentName` FROM `student`
WHERE StudentName LIKE '%嘉%';



===================IN(具体的一个或者多个值)===========================
-- 查询1001 1002 1003 学员信息
SELECT `StudentNo`,`StudentName` FROM `student`
WHERE StudentNo = 1001
SELECT `StudentNo`,`StudentName` FROM `student`
WHERE StudentNo = 1002
SELECT `StudentNo`,`StudentName` FROM `student`
WHERE StudentNo = 1003

SELECT `StudentNo`,`StudentName` FROM `student`
WHERE StudentNo IN (1001,1002,1003);

-- 查询在北京的学生
SELECT `StudentNo`,`StudentName` FROM `student`
WHERE `Address` IN('安徽','河南洛阳');


===================NULL NOT NULL===================================
-- 查询地址为空的学生 null ''
SELECT `StudentNo`,`StudentName` FROM `student`
WHERE address=''OR address IS NULL

-- 查询有出生日期的同学  不为空
SELECT `StudentNo`,`StudentName` FROM `student`
WHERE `BornDate` IS NOT NULL;




```

### 4.4 联表查询

> JOIN 对比

![](C:\Users\Administrator\Desktop\第二阶段\img\20200708013553742.png)

![](C:\Users\Administrator\Desktop\第二阶段\img\20200708013558863.png)

```sql
======================联表查询 join ==============================
-- 查询参加考试的同学 （学号，姓名，考试编号，分数）

SELECT * FROM student 
SELECT * FROM result

/*
1. 分析需求，分析查询的字段来自哪些表
2.确定使用哪种连接查询？7种
确定交叉点（这两个表中哪个数据是相同的）
判断的条件： 学生表中 studentNo = 成绩表中 studentNo 

*/

-- JION（表） ON （判断的条件）连接查询
-- where 等值查询
SELECT studentNo,studentName,SubjectNo,StudentResult
FROM student AS s
INNER JOIN result AS r
WHERE s.studentNo=r.studentNo

--Right Join
SELECT s.studentNo,studentName,SubjectNo,StudentResult
FROM student AS s
RIGHT JOIN result AS r
ON s.studentNo = r.studentNo

--LEFT Join
SELECT s.studentNo,studentName,SubjectNo,StudentResult
FROM student AS s
LEFT JOIN result AS r
ON s.studentNo = r.studentNo



```

| 操作       | 描述                                         |
| ---------- | -------------------------------------------- |
| Inner join | 如果表中至少有一个匹配，就返回行             |
| left join  | 即使左表中没有匹配，也会从左表中返回所有的值 |
| right jion | 即使右表中没有匹配，也会从右表中返回所有的值 |

```sql
-- 查询考的同学
SELECT s.studentNo,studentName,SubjectNo,StudentResult
FROM student AS s
LEFT JOIN result AS r
ON s.studentNo = r.studentNo
WHERE StudentResult IS NULL

-- 查询了参加考试同学的信息：学号：学生姓名：科目名：分数
SELECT s.`studentNo`,`studentName`,`SubjectName`,`studentResult`
FROM student s
RIGHT JOIN result r
ON r.studentNo=s.studentNo
INNER JOIN `subject` sub
ON r.SubjectNo=sub.SubjectNo

-- 我要查询哪些数据 SELECT ....
-- 从哪几个表中查 FROM 表 xxx JOIN 连接的表 ON 交叉条件
-- 假设存在一中多张表查询，先查询两章表，然后再慢慢增加

--FROM a LEFT JOIN b   左为准
--FROM a RIGHT JOIN b	右为准



```

> 自连接

自己的表跟自己的表连接，核心：**一张表拆为两张一样的表**

父类

| categoryid | categoryName |
| ---------- | ------------ |
| 2          | 信息技术     |
| 3          | 软件开发     |
| 5          | 美术设计     |

子类

| pid  | categoryid | categoryName |
| ---- | ---------- | ------------ |
| 3    | 4          | 数据库       |
| 2    | 8          | 办公信息     |
| 3    | 6          | web开发      |
| 5    | 7          | ps技术       |

操作：查询父类对应子类关系

| 父类     | 子类     |
| -------- | -------- |
| 信息技术 | 办公信息 |
| 软件开发 | 数据库   |
| 软件开发 | web开发  |
| 美术设计 | ps技术   |

```sql
-- 查询父子信息

SELECT a.`categroryName` AS `父栏目`,b.`categroryName` AS `子栏目`
FROM `catgroy` AS a,`catgroy` AS b
WHERE a.`categoryid`=b.`pid`


-- 查询学员所属的年级（学号，学生的姓名，年级）
SELECT 	studentNo,studentName,gradeName
FROM student s
INNER JOIN `grade` g
ON s.`GradeId`=g.`GradeId`


```

### 4.5分页和排序

```sql
============================分页 limit 和排序order by=================


-- 排序：  升序ASC  降序  DESC
SELECT  xx
FROM xx
JOIN xx
WHERE  xx
ORDER BY  xx
ASC   ||  DESC

分页
-- 为什么要分页
-- 缓解数据库压力，给人的体验更好


-- 分页，每页显示五条数据

-- 语法： limit 当前页，页面的大小
-- limit 0,5 1-5
-- limit 1,5 1-5
-- limit 6,5
SELECT s.`StudentNo`,`StudentName`,`SubjectName`,`StudentResult`
FROM student s
INNER JOIN `result` r
ON s.`StudentNo`=r.`StudentNo`
INNER JOIN `subject` sub
ON r.`subjectNo`=sub.`subjectNo`
WHERE subjectName='数据结构-1'
ORDER BY StudentResult ASC
LIMIT 0,5

-- 第一页 limit 0,5
-- 第二页 limit 5,5
-- 第三页 limit 10,5
-- 第N页 limit 5*（n-1）,5





语法 limit(查询起始下标，pagesize)

```

### 4.6 子查询

where (这个值是计算出来的)

本质：`在where语句中嵌套一个子查询语句`

```sql
-- ===========================where=========================

-- 1.查询 数据库结构-1的所有考试结构（学号，科目编号，成绩） 降序
-- 方式一： 连接查询
SELECT `StudentNo`,r.`SubjectName`,`StudentResult`
FROM `result` r
INNER JOIN `subject` sub
ON r.SubjectNo = sun.SubjectNo
WHERE subjectName = '数据库结构-1'
ORDER BY StudentResult DESC

-- 方式二：使用子查询(由里及外)
SELECT `StudentNo`,r.`SubjectName`,`StudentResult`
FROM `result`
WHERE StudentNo=(
	SELECT SubjectNo FROM  `subject` 
    WHERE SubjectName = '数据库结构-1'
)
ORDER BY StudentResult DESC


-- 分数不少于80分的学生的学号和姓名
SELECT DISTINCT s.`StudentNo`,`StudentName`
FROM student s
INNER JOIN result r
ON r.StudentNo = s.StudentNo
WHERE StudentResult>=80

-- 在这个基础上 增加一个科目 ，高等数学-2
SELECT DISTINCT s.`StudentNo`,`StudentName`
FROM student s
INNER JOIN result r
ON r.StudentNo = s.StudentNo
WHERE StudentResult>=80 AND `SubjectNo`=(
    SELECT Subject FROM `subject`
    WHERE SubjectName='高等数学-2'
)

-- 查询课程为 高等数学-2 且分数不小于80分的同学的学号和姓名
SELECT s.`StudentNo`,`StudentName`
FROM student s
INNER JOIN result r
ON s.StudentNo = r.StudentNo
INNER JOIN `subject` sub
ON r.`SubjectName`='高等数学-2'
WHERE `SubjectaName`='高等数学-2' AND StudentResult >=80


-- 再改造 (由里即外)
SELECT `StudentNo`,`StudentName` FROM student
WHERE StudentNo IN(
SELECT StudentNo result WHERE StudentResult >80 AND SubjectNo =(
SELECT SubjectNo FROM `subject` WHERE `SubjectaName`='高等数学-2'
)
)


```

### 4.7 分组

```sql
-- 查询不同课程的平均分，最高分，最低分，平均分大于80
-- 核心：（根据不同的课程分组）

SELECT `SubjectName`,AVG(StudentResult),MAX(StudentResult)
FROM result r
INNER JOIN `Subject` sub
ON r.SubjectNo=sub.SubjectNo

GROUP BY r.SubjectNo -- 通过什么字段来分组
HAVING AVG(StudentResult)>80




```

# 5、MySQL函数

### 5.1 常用函数

```sql
-- 数学运算

SELECT ABS(-8) -- 绝对值
SELECT CEILING(9.4) -- 向上取整
SELECT FLOOR(9.4)  -- 向下取整
SELECT RAND() -- 返回0-1随机数
SELECT SIGN(-10) -- 判断一个数的符号 0-0 负数返回-1 正数返回1

-- 字符串函数
SELECT CHAR_LENGTH('2323232') -- 返回字符串长度
SELECT CONCAT('我','233') -- 拼接字符串
SELECT INSERT('java',1,2,'cccc') -- 从某个位置开始替换某个长度
SELECT UPPER('abc') 
SELECT LOWER('ABC')
SELECT REPLACE('坚持就能成功','坚持','努力')

-- 查询姓 周 的同学 ，改成邹
SELECT REPLACE(studentname,'周','邹') FROM student
WHERE studentname LIKE '周%'

-- 时间跟日期函数（记住）
SELECT CURRENT_DATE() -- 获取当前日期
SELECT CURDATE() -- 获取当前日期
SELECT NOW() -- 获取当前日期
SELECT LOCATIME()  -- 本地时间
SELECT SYSDATE()  -- 系统时间

SELECT YEAR(NOW())
SELECT MONTH(NOW())
SELECT DAY(NOW())
SELECT HOUR(NOW())
SELECT MINUTE(NOW())
SELECT SECOND(NOW())

-- 系统
SELECT SYSTEM_USER()
SELECT USER()
SELECT VERSION()


```

### 5.2 聚合函数（常用）

| 函数名称    | 描述   |
| ----------- | ------ |
| **COUNT()** | 计数   |
| SUM()       | 求和   |
| AVG()       | 平均值 |
| MAX()       | 最大值 |
| MIN()       | 最小值 |
| …           |        |

### 5.3 数据库级别MD5加密（拓展）

什么是MD5

主要增强算法复杂度不可逆性。

MD5不可逆，具体的MD5是一样的

MD5破解原理，背后有一个字典，MD5加密后的值，加密前的值

```sql
CREATE TABLE `testmd5`(
`id` INT(4) NOT NULL,
`name` VARCHAR(20) NOT NULL,
`pwd` VARCHAR(50) NOT NULL,
PRIMARY KEY (`id`)

)ENGINE=INNODB DEFAULT CHARSET=UTF8


-- 明文密码
INSERT INTO testmd5 VALUES(1,'张三','123456'),(2,'李四','123456'),(3,'王五','123456')

-- 加密
UPDATE testmd5 SET pwd=MD5(pwd) WHERE id =1
UPDATE testmd5 SET pwd=MD5(pwd) WHERE id !=1  -- 加密全部

-- 插入时加密

INSERT INTO testmd5 VALUES(4,'小明',MD5('123456'))
INSERT INTO testmd5 VALUES(5,'红',MD5('123456'))

-- 如何校验，将用户传递过来的密码，进行MD5加密，然后对比加密后的值
SELECT * FROM testmd5 WHERE `name`='红' AND pwd=MD5('123456')

```

# 6、事务(需要重新备课)

### 6.1 什么是事务

**要么都成功，要么都失败**

1. SQL执行， A给B转账 A 1000–> 200 B200
2. SQL 执行， B收到A的钱 A800 — B400

将一组SQL放在一个批次中执行

> 事务原则 ： ACID原则 原子性，一致性，隔离性，持久性 （脏读，幻读…）

**原子性**（Atomicity）

要么都成功，要么都失败

**一致性（Consistency）**

事务前后的数据完整性要保持一致

**持久性（Durability）**–事务提交

事务一旦提交就不可逆转，被持久化到数据库中

**隔离性**

事务产生多并发时，互不干扰

> 隔离产生的问题

### 脏读：

指一个事务读取了另外一个事务未提交的数据。

### 不可重复读：

在一个事务内读取表中的某一行数据，多次读取结果不同。（这个不一定是错误，只是某些场合不对）

### 虚读(幻读)

是指在一个事务内读取到了别的事务插入的数据，导致前后读取不一致。
（一般是行影响，多了一行）

执行事务

```sql
-- mysql 自动开启事务提交
SET autocommit=0 -- 关闭
SET autocommit=1 -- 开启（默认的）

-- 手动处理事务
SET autocommit =0 -- 关闭自动提交

-- 事务开启

START TRANSACTION -- 标记一个事务的开始，从这个之后的SQP都在同一个事务内

INSERT XX
INSERT XX

-- 提交 ： 持久化(成功)
COMMIT 
-- 回滚：  回到原来的样子（失败）
ROLLBACK
-- 事务结束
SET autocommit = 1 -- 开启自动提交
-- 了解
SAVEPOINT 保存点名称 -- 设置一个事务的保存点
ROLLBACK TO SAVEPOINT 保存点名 -- 回滚到保存点
RELEASE SAVEPOINT 保存点 -- 删除保存点


```

# 7、索引

> MySQL索引的建立对于MySQL的高效运行是很重要的，索引可以大大提高MySQL的检索速度。

### 7.1索引的分类

> 在一个表中，主键索引只能有一个，唯一索引可以有多个

**主键索引 （PRIMARY KEY）**
唯一的标识，主键不可重复，只能有一个列作为主键
**唯一索引 （UNIQUE KEY）**
避免重复的列出现，唯一索引可以重复，多个列都可以标识唯一索引
**常规索引（KEY/INDEX）**
默认的，index,key关键字来设置
**全文索引（FULLTEXT）**
在特点的数据库引擎下才有，MyISAM
快速定位数据

```sql
-- 索引的使用
-- 1.在创建表的时候给字段增加索引
-- 2.创建完毕后，增加索引

-- 显示所有的索引信息
SHOW INDEX FROM 表

-- 增加一个索引
ALTER TABLE 表 ADD FULLTEXT INDEX 索引名（字段名）

-- EXPLAIN 分析sql执行状况
EXPLAIN SELECT * FROM student -- 非全文索引




```

### 7.2 测试索引

```sql
CREATE TABLE `app_user` (
`id` BIGINT(20) UNSIGNED NOT NULL AUTO_INCREMENT,
`name` VARCHAR(50) DEFAULT '',
`email` VARCHAR(50) NOT NULL,
`phone` VARCHAR(20) DEFAULT '',
`gender` TINYINT(4) UNSIGNED DEFAULT '0',
`password` VARCHAR(100) NOT NULL DEFAULT '',
`age` TINYINT(4) DEFAULT NULL,
`create_time` DATETIME DEFAULT CURRENT_TIMESTAMP,
`update_time` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
PRIMARY KEY (`id`)
) ENGINE=INNODB DEFAULT CHARSET=utf8

-- 插入100万数据
DELIMITER $$ --  写函数之前必写
CREATE FUNCTION mock_data()
RETURNS INT 
BEGIN
DECLARE num INT DEFAULT 1000000;
DECLARE i INT DEFAULT 0;

WHILE i<num DO
-- 插入语句
INSERT INTO app_user(`name`,`email`,`phone`,`gender`,`password`,`age`)
VALUE(CONCAT('用户',i),'534240118@qq.com',FLOOR (CONCAT('18',RAND()*9999999)),FLOOR (RAND()*2),
UUID(),FLOOR (RAND()*100));

SET i = i+1;
END WHILE;
RETURN i;


END;

INSERT INTO app_user(`name`,`email`,`phone`,`gender`,`password`,`age`)
VALUE(CONCAT('用户',i),'534240118@qq.com',FLOOR (CONCAT('18',RAND()*9999999)),FLOOR (RAND()*2),
UUID(),FLOOR (RAND()*100))


SELECT mock_data();

SELECT * FROM app_user WHERE `name`='用户9999' -- 接近半秒

EXPLAIN SELECT * FROM app_user WHERE `name`='用户9999'  -- 查询99999条记录

-- id _ 表名_字段名
-- create index on 字段
CREATE INDEX id_app_user_name ON app_user(`name`); -- 0.001 s
EXPLAIN SELECT * FROM app_user WHERE `name`='用户9999'  -- 查询一条记录

```

索引在小数据的时候，用处不大，但是在大数据的时候，区别十分明显

### 7.3 索引原则

- 索引不是越多越好
- 不要对经常变动的数据加索引
- 小数据量的表不需要加索引
- 索引一般加在常用来查询的字段上

**索引的数据结构**

Hash 类型的索引

Btree: 默认innodb 的数据结构

阅读： http://blog.codinglabs.org/articles/theory-of-mysql-index.html

# 8、权限管理和备份

### 8.1用户管理

> SQL命令操作

用户表：mysql.user

本质：对这张表进行，增删改查

```sql
-- 创建用户  CREATE USER 用户名 IDENTIFIED BY '密码'
CREATE USER sanjin IDENTIFIED BY '123456'

-- 修改密码（修改当前密码）
SET PASSWORD = PASSWORD('111111')


-- 修改密码（修改指定用户密码）

SET PASSWORD FOR sanjin = PASSWORD('111111')


-- 重命名  rename user 原名字 to 新名字
RENAME USER sanjin TO sanjin2

-- 用户授权   ALL PRIVILEGES 全部的权限   库，表
-- ALL PRIVILEGES 除了给别人授权，其他都能干
GRANT ALL PRIVILEGES ON *.* TO sanjin2

-- 查询权限
SHOW GRANTS FOR sanjin2  -- 查看指定用户的权限
SHOW GRANTS FOR root@localhost


-- 撤销权限 REVOKE 哪些权限，在哪个库撤销，给谁撤销
REVOKE ALL PRIVILEGES ON *.* FROM sanjin2

-- 删除用户
DROP USER sanjin2


```

### 8.2 MySQL备份

为什么备份：

- 保证重要数据不丢失
- 数据转移

MySQL数据库备份的方式

- 直接拷贝物理文件
- 在SQLyog这种可视化工具中手动导出
  - 在想要导出的表或者库中，右键选择备份和导出



# 9、规范数据库设计

**当数据库比较复杂的时候，我们就需要设计了**

糟糕的数据库设计：

- 数据冗余，浪费空间
- 数据库插入和删除都会麻烦，异常【屏蔽使用物理外键】
- 程序的性能差

良好的数据库设计：

- 节省内存空间
- 保证数据库的完整性
- 方便我们开发系统

软件开发中，关于数据库的设计

- 分析需求：分析业务和需要处理的数据库的需求
- 概要设计：设计关系图 E-R图

**设计数据库的步骤（个人博客）**

- 收集信息，分析需求
  - 用户表（用户登录注销，用户的个人信息，写博客，创建分类）
  - 分类表（文章分类，谁创建的）
  - 文章表（文章的信息）
  - 友链表（友链信息）
  - 自定义表（系统信息，某个关键的字，或者某些主字段）
  - 说说表（发表心情…id ,content ,time）

- 标识实体（把需求落地到每个字段）
- 标识实体之间的关系
  - 写博客 user–>blog
  - 创建分类 user–>category
  - 关注 user–>user
  - 友链–>links
  - 评论 user–>user

### 9.2三大范式

为什么需要数据规范化？

- 信息重复
- 更新异常
- 插入异常
- 删除异常
  - 无法正常显示异常
- 删除异常
  - 丢失有效的信息

**三大范式**

第一范式（1NF）

原子性：保证每一列不可再分

第二范式（2NF）

前提：满足第一范式

每张表只描述一件事情

第三范式（3NF）

前提：满足第一范式和第二范式

第三范式需要确保数据表中的每一列数据都和主键直接相关，而不能间接相关。

（规范数据库的设计）

规范性和性能的问题


关联查询的表，不得超过三张表

- 考虑商业化的需求和目标（成本和用户体验） 数据库的性能更加重要
- 再规范性能的问题的时候，需要适当的考虑一下，规范性
- 故意给某些表加一些冗余的字段（从多表，变成单表）
- 故意增加一些计算列（从大数据量降低为小数据量的查询：索引）