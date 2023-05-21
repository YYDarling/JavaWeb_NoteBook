# DataBase 不在乎大小写的问题

## 1. DDL 

```mysql
/*
1. create database 数据库名
*/
create database study

/*
2. 为了能够支持中文，我们在创建时可以设定编码格式：
CREATE DATABASE IF NOT EXISTS 数据库名 DEFAULT CHARSET utf8 COLLATE utf8_general_ci;
*/
CREATE DATABASE IF NOT EXISTS studey DEFAULT CHARSET utf8 COLLATE utf8_general_ci;

/*
数据库删除
*/
drop database 数据库名

/*
3. 切换数据库， 看你要建立在哪里, defalut 是mysql
*/
use study

/*
4. create table 表名(列名 数据类型[列级约束条件],
             列名 数据类型[列级约束条件],
             ...
             [,表级约束条件])

##添加表级约束条件
##[CONSTRAINT <外键名>] FOREIGN KEY 字段名 [，字段名2，…] REFERENCES <主表名> 主键列1 [，主键列2，…]
*/
create table student(sid int primary key, 
                    name varchar(10) not null, 
                    sex enum('male', 'female') not null default 'femalw');
                    
create table teacher(tid int primary key, 
                    name varchar(10) not null);

create table teach(tid int not null, 
                   sid int not null,
           
                   CONSTRAINT 'f_tid' FOREIGN KEY ('tid') REFERENCES 'study'.'teacher'('tid');
                   CONSTRAINT 's_tid' FOREIGN KEY ('sid') REFERENCES 'study'.'student'('sid');
                   
/*
修改表
ALTER TABLE 表名[ADD 新列名 数据类型[列级约束条件]]
                             [DROP COLUMN 列名[restrict|cascade]]
                             [ALTER COLUMN 列名 新数据类型]                   
*/
ALTER TABLE teacher add sex enum('male','female') not null default 'male'
                             
                   

```



## 2. DML 

```mysql
/*
1. 插入数据
INSERT INTO 表名 VALUES(值1, 值2, 值3)
*/
INSERT INTO student VALUES(19909，'feifei', 'male')；
INSERT INTO student(sid, name) VALUES(19909，'feifei')； ##指定上插入默认值
INSERT INTO student VALUES(19909，'feifei', 'male'), (8989, 'huahua', 'female')；

/*
2. 更新数据
update
UPDATE 表名 SET 列名=值,... WHERE 条件
*/
UPDATE student SET name = 'xiaohua'WHERE sid= 1829 ;

/*
3.删除数据
DELETE FROM 表名
DELETE FROM 表名 WHERE 条件
*/
DELETE FROM student WHERE sid = 111



```

## 3.DQL

```mysql
/*
1.
-- 指定查询某一列数据
SELECT 列名[,列名] FROM 表名
-- 会以别名显示此列
SELECT 列名 别名 FROM 表名
-- 查询所有的列数据
SELECT * FROM 表名
-- 只查询不重复的值
SELECT DISTINCT 列名 FROM 表名
--
SELECT * FROM 表名 WHERE 条件

2.
一般的比较运算符，包括=、>、<、>=、<=、!=等。
是否在集合中：in、not in
字符模糊匹配：like，not like
多重条件连接查询：and、or、not

3. 
--排序查询
SELECT * FROM 表名 WHERE 条件 ORDER BY 列名 ASC|DESC

4. 
--添加多个排序
SELECT * FROM 表名 WHERE 条件 ORDER BY 列名1 ASC|DESC, 列名2 ASC|DESC

5. 
聚集函数
count([distinct]*)统计所有的行数（distinct表示去重再统计，下同）
count([distinct]列名)统计某列的值总和
sum([distinct]列名)求一列的和（注意必须是数字类型的）
avg([distinct]列名)求一列的平均值（注意必须是数字类型）
max([distinct]列名)求一列的最大值
min([distinct]列名)求一列的最小值

*/

Select * from student  ##查询所有列数据
select name, sex from student  ##查询name, sex这两列
select distinct name, sex from student #只查询不重复的值
select * from student where sex = 'male' ;#查询
select * from student where name not in ('Ming', 'Gang');
select * from student where sid like %03; ##以03结尾的student ID， 03%以03开头，%03%其中包含03
select * from student where sid like %03 and sex = 'male';

SELECT * FROM student WHERE sid like 03% ORDER BY sid DESC; 

SELECT * FROM student WHERE sid like 03% ORDER BY sex Asc, sid DESC; 
##先按照性别进行排序， 再按照sid进行内排序


SELECT count(*) FROM student; 
SELECT count(distinct sex) FROM student;
SELECT count(*) , sex FROM student group by sex;  ##聚合函数分组
SELECT count(*) , sex FROM student group by sex having sex = 'male';  ##聚合函数分组, 限定男生
SELECT * FROM student LIMIT 3; ##限定数量为前三
SELECT * FROM student LIMIT 0，3; ##限定数量， 可以实现分页的效果


/*
多表查询
直接这样查询会得到两张表的笛卡尔积，也就是每一项数据和另一张表的每一项数据都结合一次，会产生庞大的数据。使用where
*/

select * from student, teacher;
##SELECT * FROM 表1, 表2 WHERE 条件
select * from student, teacher where teacher.tid = 1;

select * from student inner join teach on student.sid = teach.sid;
select * from student left join teach on student.sid = teach.sid;
select * from student right join teach on student.sid = teach.sid
											left join teacher on teach.tid = teacher.tid;
											
/*
嵌套查询, 查找哪个老师教了哪几个学生
*/
select * from student right join teach on student.sid = teach.sid
											left join teacher on teach.tid = teacher.tid where teacher.name = 'Zhang';
											
											
											多表查询要多看一下啊

```



## 4.DCL

```mysql
/*
CREATE USER 用户名 identified by 密码;

*/
```

