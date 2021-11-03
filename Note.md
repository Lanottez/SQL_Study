第一章：数据库和SQL

```
DDL(Data Definition Language): CREATE, DROP,ALTER
DML(Data Manipulation Language): SELECT, INSERT, UPDATE, DELETE ***
DCL(Data Control Language): COMMIT,ROLLBACK,GRANT,REVOKE
```



创建数据库：

```
CREATE DATABASE <数据库名称>;
```



创建表：

```
CREATE TABLE <表名称>;
```



创建Product表的CREATE TABLE语句：

```
CREATE TABLE Product(
product_id		 CHAR(4)			 NOT NULL,
product_name	 VARCHAR(100)		 NOT NULL,
product_type	 VARCHAR(100)		 NOT NULL,
sale_price		 Integer			 ,
purchase_price	 Integer			 ,
regist_date		 Date				 ,
PRIMARY KEY (product_id));
```



删除表

````
DROP TABLE <表名>
````



添加列

```
ALTER TABLE <表名> ADD COLUMN <列名> <列的定义>
```



删除列

```
ALTER TABLE <表名> DROP COLUMN <列名>
```

