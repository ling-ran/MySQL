# SQL语言分类
 
 分类  |  全称 | 说明
--------|---------|--------
DDL  |Data Definition Language |数据定义语言，用来定义数据库对象（数据库，表，字段）
DML |Data Manipulation Language| 数据操作语言，用来对数据表的数据进行增删改
DQL |Data Query Language   |数据查询语言，用来查询数据库中的表的记录
DCL |Data Control Language |数据控制语言，用来船舰新的数据库用户、控制数据库的访问权限

 
 ## MySQL数据类型
 - **数值类型**
 
 类型  |  大小 | 有符号（sigend)范围|  无符号（unsigned)范围  |  描述
 ------- | -------| -----------------------------|          ----------------------------    |----------
 **tinyint**| 1 byte|  (-128,127)               |  (0,255)            |小整数值
 **smallint** | 2 byte | (-32768, 32767)|  (0, 65535)  |     大整数值                           
**mediumint** |3 bytes         |(-8388608, 8388607) |(0, 16777215)  |大整数值
**int或integer**  |  4 bytes   |   (-2147483648, 2147483647) | (0, 4294967295) |大整数值
**bigint**     |  8 byte    | (-2 ^63 ,2 ^63 - 1)     |(0, 2^64 - 1)   |  极大整数值
**float**     |  4 byte    |(-3.402823466 E+38, 3.402823466351 E+38) |0 和 (1.175494351 E-38, 3.402823466 E+38)|单精度浮点数值
**double**  | 8 byte   | (-1.7976931348623157 E+308, 1.7976931348623157 E+308) |0 和 (2.2250738585072014 E-308, 1.7976931348623157 E+308) |双精度浮点数值
**declmal**|              |依赖于M（精度）和D（标度）的值  |依赖于M（精度）和D（标度）的值|小数值（精确小数点）

-  **字符串类型**

类型  |  大小 |  描述
-------| ---------|--------
CHAR |0-255 bytes  |定长字符串
VARCHAR |  0-65535 bytes  |变长字符串
TINYBLOB | 0-255 bytes   |不超过255个字符的二进制数据
TINYTEXT|0-255 bYtes|短文本宇符串
BLOB  |0-65 535 bytes  |二进制形式的长文本数据  
TEXT |0-65 535 bytes    |长文本数据
MEDIUMBIOB |0-16 777 215 bytes |二进制形式的中等长度文本数据
MEDIUMTEXT |0-16 777 215 bYtes |中等长度文本数据
LONGBIOB  |0-4 294 967 295 bytes |二进制形式的极大文本数捐
LONGTEXT |0-4 294 967 295 bytes |极大文本数据

- **日期类型**

类型 | 大小 |   范围   |   格式   |   描述  
------|--------|-----------|-----------|-----------
DATA |   3   |1000-01-01 至 9999-12-31  |YYYK-MM-DD |日期型
TIME |   3   |-838:59:59 至 838:59:59   |   HH:MM:SS     |时间值或持续时间
YEAR |  1   |1901 至 2155                  | YYYY                 |年份值
DATETINE |   8   |  1000-01-01 00:00:00 至 9999-12-31 23: 59:59   |  YYYY-MM-DD HH:M:SS  |混合日期和时间值
TIMESTAMP | 4 |  1970-01-01 00:00:01 至 2038-01-19 03: 14:07    |  YYYY-MM-DD HH:M:SS |混合日期和时间值, 时间戳
-------------------------------------------------------------------------------------------------------------------------

## DDL
- 查询
  - 查询所有数据库
  
  `SHOW DATABASES;`
  - 查询当前数据库
  
  `SELECT DATABAES;` 
   - 创建

   `CREATE DATABASE [IF NOT EXISTS] 数据库名 [DEFAULT CHARS£T 字符集 [ COLLATE 排序规则];`
   - 删除

    `DROP DATABASE [ IF EXISTS] 数据库名;`
    - 使用

    `USE 数据库名`

--------------------------------------------------------------------------------------------------------------
- DDL-表操作-查询
   - 查询当前的数据库所用表
  
    `SHOW TABLES`
  
   - 查询表结构
 
   `DESC表名`
 
   - 查询指定表的建表语句 

    `SHOW CREATE TABLE 表名`

 -----------------------------------------------------------------------------------------------------------------
 - DDL-表操作-创建
 
```sql
CREATE TABLE user（
字段  字段类型[COMMENT 字段注释]
id int comment'编号'
name varchar(50) comment'姓名'
age int comment'年龄'
gender varchar(1) comment'性别'
）comment'用户表';
```

- DDL-表操作-修改
  - **添加字段**
  
   `ALTER TABLE 表名 ADD 字段名 类型 (长度) [COMMENT 注释] [约束];`
 
   - 案例：为emp表增加一个新的字段" 昵称" 为nickname, 类型为varchar(20)
  
   `ALTER TABLE emp ADD nickname varchar(20) COMMENT '昵称';`
 
    - **修改数据类型**
   
   `ALTER TABLE 表名 MODIFY 字段名 新数据类型 (长度);`
 
    - **修改字段名和字段类型**
   
   `ALTER TABLE 表名 CHANGE 旧日字段名 新字段名 类型 (长度) [COMMENT 注释] [约束];`
   - 案例：将emp表的nickname字段修改为username, 类型为varchar(30)
   
   `ALTER TABLE emp CHANGE nickname usernamevarchar(30) COMMENT ' 昵称';`
   - **删除字段**

  `ALTER TABLE 表名 DROP 字段名;`
   - 案例：将emp表的宇段username删除
   
   `ALTER TABLE emp DROP username;`
   - **修改表名**
   
   `ALTER TABLE 表名 RENAME TO 新表名;`
   - 案例：将emp表的表名修改为 employee
   
   `ALTER TABLE emp RENAME TO employee;`
 ---------------------------------------------------------------------------------------------------------------------
 - DDL-表操作-删除
   - 删除表
   
   `DROP TABLE [IF EXISTS] 表名;`
   
   - 删除指定表, 并重新创建该表
   
   `TRUNCATE TABLE 表名;`
   
   - 注意: 在删除表时, 表中的全部数据也会被删除
 --------------------------------------------------------------------------------------------------------------------- 
## DML
  - DML-添加数据
    - 给指定字段添加数据
    
    `INSERT INTO 表名 (字段名1, 字段名2, ..) VALUES (值1, 值2, .);`
    
    - 给全部字段添加数据
    
    `INSERT INTO 表名 VALUES (值1, 值2, ..);`
    
    - 批量添加数据
    
    `INSERT INTO 表名 (字段名1, 字段名2, .) VALUES (值1, 值2, ..), (值1, 值2, ..), (值1, 值2,.);`
    
    `INSERT INTO 表名 VALUES (值1, 值2, :.), (值1, 值2, :.), (值1, 值2, :.);`
> 注意：
> - 插入数据时, 指定的字段顺序需要与值的顺序是一一对应的
> - 字符串和日期型数据应该包含在引号中
> - 插入的数据大小, 应该在字段的规定范围内
---------------------------------------------------------------------------------------------------------------------------------
## DQL数据查询语言
![执行顺序](https://img-blog.csdnimg.cn/f64446b8525042c888ce58348b63bf50.jpeg#pic_center)

- DQL-基本查询
  - 查询多个字段

	`SELECT 字段1, 字段2, 字段3. FROM 表名` 
    
    `SELECT * FROM 表名;`

  - 设置别名

	`SELECT 字段1 [AS 别名1], 字段2 [AS 别名2]...FROM 表名;`                                                                             
     
  - 去除重复记录

	`SELECT DISTINCT 字段列表 FROM 表名;` 

- DQL-条件查询
  -  语法：`SELECT 字段列表 FROM 表名 WHERE 条件列表;`
  -   条件

比较运算符 |  功能
--------------- | --------
\>               | 大于                                                                               
\>=             |大于等于
\<             |小于
\<=           |小于等于
=              |等于
<>或！=  |不等于
BETWEEN...AND... |在某个范围之内(含最小, 最大值)
IN()         | 在in之后的列表中的值, 多选一
LIKE 占位符 | 模糊 匹配("_"匹配单个字符, "%"匹配任意个字符)
IS NULL |  是NULL

逻辑运算符 | 功能
---------------|---------
AND或&& | 并且（多个条件任意一个成立）
OR或\|\|    |或者（多个条件任意一个成立）
NOT或！ |非，不是

- 1. 查询年龄等于20的员工

	`select * from emp where age = 88;`

- 2.  查询年龄小于 20 的员工信息

	`select * from emp where age < 20;`

- 3. 查询年龄小于等于 20 的员工信息

	`select * from emp where age <= 20;`

- 4. 查询没有身份证号的员工信息

	`select * from emp where idcard is null;`

- 5. 查询有身份证号的员工信息

  `select * from emp where idcard is not null;`

- 6. 查询年龄不等于88的员工信息

	`select from emp where age !=88;`

	`select from emp where age <88;`
	
- 7. 查询年龄在15岁（包含）到20岁（包含）之间的员工信息

	`select from emp where age >15 &age <20;`

	`select from emp where age >=15 and age <=20;`

	`select from emp where age between 15 and 20;`

 - 8. 查询性别为女且年龄小于25岁的员工信息

	`select from emp where gender =and age 25;`
	
- 9. 查询年龄等于18或20或40的员工信息

	`select from emp where age 18 or age 20 or age =40;`
	
	`select from emp where age  in(18,20,40)`

- 10. 查询姓名为两个字的员工信息_%

	`select from emp where name like`

- 11. 查询身份证号最后一位是X的员工信息

	`select from emp where idcard like '%x';`
	
	`select from emp where idcard like'_________________x'`









## 六种约束
主键约束primary key
NOT NULL /NULL
检查约束-一在MySQL中不支持
默认值约束default
唯一性约束unique
外键约束foreign key

----------------------------
>根据已有的数据表创建新的表
- 1、复制表整个结构
CREATE TABLE student1 LIKE student;
- 2、复制表整个结构和数据
CREATE TABLE student2 SELECT FROM student;
- 3、复制表的部分结构
CREATE TABLE education1 SELECT id,school FROM education WHERE 1 !1;
- 4、复制表的部分结构和部分数据
CREATE TABLE education2 SELECT id,school FROM education WHERE条件；

---------------------------------------
>修改表的结构
- 1、先删除表，再重建（只适用于没有数据情况）
DROP TABLE表名；（不能删除有主外键关系中的主表）
CREATE TABEL....
- 2、采用命令完成修改ALTER动词
动词：CREATE(创建)DROP(删除)ALTER(修改)

## DDL表操作修改
- 1、增加字段
ALTER TABLE education2 ADD abc varchar(10)NOT NULL;
- 2、删除字段
ALTER TABLE education2 DROP abc;
- 3、修改字段名字，同时可以修改列的数据类型
ALTER TABLE education2 CHANGE comment abc varchar(50)
- 4、只修改列的数据类型
(1)ALTER TABLE education2 CHANGE abc abc varchar(100);
(2)ALTER TABLE education2 MODIFY abc varchar(50);
- 5、修改表名
(1)ALTER TABLE education2 RENAME edu;
(2)RENAME TABLE education1 TO educate;
- 6、修改其它属性（存储引擎，字符集）
ALTER TABLE edu ENGINE=MyISAM;
ALTER TABLE edu default charset=gbk
- 7、修改表的约束
- (1)添加约束
ALTER TABLE edu ADD CONSTRAINT pk_id primary key(id);
- (2)删除约束
ALTER TABLE edu DROP FOREIGN KEY约束名；
