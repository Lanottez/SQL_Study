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

###  

## 第三章：聚合和排序

###### 计算全部\具体数据的行数 (COUNT)

```
SELECT COUNT(*)
  FROM Product;
  
SELECT COUNT(purchase_price)
  FROM Product;
```



###### 合计值 (SUM)

```
SELECT SUM(sale_price)
  FROM Product;
```



###### 平均值 (AVG)

```
SELECT AVG(sale_price)
  FROM Product;
```



###### 最大值\最小值 (MAX\MIN)

```
SELECT MAX(sale_price), MIN(purchase_price)
  FROM Product;
```



###### 计算去除重复数据后的数据行数 

```
SELECT COUNT(DISTINCT product_type)
  FROM Product;
```



###### 按照商品种类统计数据行数 (GROUP BY)

```
SELECT product_type, COUNT(*)
  FROM Product
 GROUP BY product_type;
 
\* 
常见错误：
1. 在SELECT字句中书写了多余的列
2. 在GROUP BY子句中写了列的别名（PostgreSQL除外）
3. 认为GROUP BY子句的结果能排序
4. 在WHERE子句中使用聚合函数（WHERE只能指定记录（行）的条件，HAVING才可指定组的条件）
*\
```



###### 过滤后汇总处理 (WHERE, GROUP BY)

```
SELECT purchase_price,COUNT(*)
	FROM Product
	WHERE product_type = '衣服'
 GROUP BY purchase_price;
 
\*
语句顺序: SELECT -> FROM -> WHERE -> GROUP BY

执行顺序: FROM -> WHERE -> GROUP BY -> SELECT
*\
```



指定包含2行数据的组

```
SELECT product_type, COUNT(*)
  FROM Product
 GROUP BY product_type
HAVING COUNT(*) = 2;

\*
HAVING语句中只能出现常数、聚合函数、GROUP BY子句中指定的列名

语句顺序: SELECT -> FROM -> WHERE -> GROUP BY -> HAVING

执行顺序: FROM -> WHERE -> GROUP BY -> HAVING -> SELECT
*\
```



HAVING子句/WHERE子句





## 第五章：复杂查询

