## 第一章：数据库和SQL

```
DDL(Data Definition Language): CREATE, DROP,ALTER
DML(Data Manipulation Language): SELECT, INSERT, UPDATE, DELETE ***
DCL(Data Control Language): COMMIT,ROLLBACK,GRANT,REVOKE
```



###### 创建数据库

```
CREATE DATABASE <数据库名称>;
```



###### 创建表

```
CREATE TABLE <表名称>;
```



###### 删除表

````
DROP TABLE <表名>
````



###### 添加列

```
ALTER TABLE <表名> ADD COLUMN <列名> <列的定义>
```



###### 删除列

```
ALTER TABLE <表名> DROP COLUMN <列名>
```



###### 修改表格名称

```
ALTER TABLE Poduct RENAME TO Product;
```



###### 向product表中插入数据

```
BEGIN TRANSACTION;
INSERT INTO Product VALUES ('0001', 'T恤' ,'衣服', 1000, 500, '2009-09-20');
INSERT INTO Product VALUES ('0002', '打孔器', '办公用品', 500, 320, '2009-09-11');
INSERT INTO Product VALUES ('0003', '运动T恤', '衣服', 4000, 2800, NULL);
INSERT INTO Product VALUES ('0004', '菜刀', '厨房用具', 3000, 2800, '2009-09-20');
INSERT INTO Product VALUES ('0005', '高压锅', '厨房用具', 6800, 5000, '2009-01-15');
INSERT INTO Product VALUES ('0006', '叉子', '厨房用具', 500, NULL, '2009-09-20');
INSERT INTO Product VALUES ('0007', '擦菜板', '厨房用具', 880, 790, '2008-04-28');
INSERT INTO Product VALUES ('0008', '圆珠笔', '办公用品', 100, NULL, '2009-11-11');
COMMIT;
```

###### 创建Product表

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



## 第二章：查询基础

###### 查询所有的列(SELECT)

```sql
SELECT *
FROM <表名>;
```



###### 设定别名(AS)

```sql
SELECT 
product_id    AS ”商品编号“,
product_name  AS ”商品名称“,
purchase_price AS ”商品价格“
FROM Product;
```



###### 查询常数

```
SELECT 
'商品' AS string, 
38 AS number, 
'2009-02-24' AS date,
product_id, 
product_name
FROM Product;
```



###### 删除重复的数据(DISTINCT)

```
SELECT 
DISTINCT product_type
FROM Product;

SELECT 
DISTINCT product_type, regist_date
FROM Product;
```



###### 选择特定的记录(WHERE)

```
SELECT <列名>
FROM <表名>
WHERE <条件表达式>;
```







## 第五章：复杂查询

