# MySQL
## SQL语言分类
 
 分类  |  全称 | 说明
--------|---------|--------
DDL  |Data Definition Language |数据定义语言，用来定义数据库对象（数据库，表，字段）
DML |Data Manipulation Language| 数据操作语言，用来对数据表的数据进行增删改
DQL |Data Query Language   |数据查询语言，用来查询数据库中的表的记录
DCL |Data Control Language |数据控制语言，用来船舰新的数据库用户、控制数据库的访问权限

 
## MySQL数值类型
 类型  |  大小 | 有符号（sigend)范围|  无符号（unsigned)范围  |  描述
 ------- | -------| -----------------------------|          ----------------------------    |----------
 **tinyint**| 1 byte|  (-128,127)               |  (0,255)            |小整数值
 **smallint** | 2 byte | (-32768, 32767)|  (0, 65535)  |     大整数值                           
**mediumint** |3 bytes         |(-8388608, 8388607) |(0, 16777215)  |大整数值
**int或integer**  |  4 bytes   |   (-2147483648, 2147483647) | (0, 4294967295) |大整数值
**bigint**     |  8 byte    | (-2 ^63 ,2 ^63 - 1)     |(0, 2^64 - 1)   |  极大整数值
**float**     |  4 byte    |(-3.402823466 E+38, 3.402823466351 E+38) |0 和 (1.175494351 E-38, 3.402823466 E+38)|单精度浮点数值
**double**  | 8 byte   | (-1.7976931348623157 E+308, 1.7976931348623157 E+308) |0 和 (2.2250738585072014 E-308, 1.7976931348623157 E+308) |双精度浮点数值
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
