# MySQL
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
