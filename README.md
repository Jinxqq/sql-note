# sql-note

#### 一，base	

1，select

SELECT 语句用于从数据库中选取数据。																						

结果被存储在一个结果表中，称为结果集。

语法：

```sql
select cols from table
```

例如：

```sql
select * from table
```



2，distict

在表中，可能会包含重复值。有时我们希望仅仅列出不同（dist	inct）的值。

关键词 DISTINCT 可以用来过滤相同的值。

语法：

```sql
SELECT DISTINCT column_name,column_name FROM table_name;
```

例如：

```sql
SELECT DISTINCT Company FROM Orders 
```



3，where

WHERE 子句用于提取那些满足指定条件的记录。

语法：

```sql
SELECT column_name,column_name FROM table_name WHERE column_name operator value;
```

例如：

```sql
SELECT * FROM Websites WHERE country='CN';
```



4，and & or

如果第一个条件和第二个条件都成立，则 AND 运算符显示一条记录。

如果第一个条件和第二个条件中只要有一个成立，则 OR 运算符显示一条记录。

例如：

```sql
SELECT * FROM Websites
WHERE country='CN'
AND alexa > 50;	
```



5，order by

ORDER BY 关键字用于对结果集按照一个列或者多个列进行排序。

ORDER BY 关键字默认按照升序对记录进行排序。如果需要按照降序对记录进行排序，您可以使用 DESC 关键字。

语法：																																																																																																							

```mssql
SELECT column_name,column_name
FROM table_name
ORDER BY column_name,column_name ASC|DESC;
```

例如：

```sql
SELECT * FROM Websites
ORDER BY alexa;
```



6，insert

INSERT INTO 语句用于向表中插入新记录。

语法1：

```sql
INSERT INTO table_name
VALUES (value1,value2,value3,...);
```

语法2：

```sql
INSERT INTO table_name (column1,column2,column3,...)
VALUES (value1,value2,value3,...);
```

例如：

```sql
INSERT INTO Websites (name, url, alexa, country)
VALUES ('百度','https://www.baidu.com/','4','CN');
```



7，update
UPDATE 语句用于更新表中已存在的记录。
语法:
```sql
UPDATE table_name
SET column1=value1,column2=value2,...
WHERE some_column=some_value;
```
例如：
```sql
UPDATE Websites 
SET alexa='5000', country='USA' 
WHERE name='菜鸟教程';
```

8，delete

DELETE 语句用于删除表中的行。

语法:

```sql
DELETE FROM 表名称 WHERE 列名称 = 值
```

例如：

```sql
DELETE FROM Person WHERE LastName = 'Wilson' 

// delete all
DELETE FROM table_name
// or
DELETE * FROM table_name
```



#### 2，senior	

**1 ,TOP 子句**

TOP 子句用于规定要返回的记录的数目。

对于拥有数千条记录的大型表来说，TOP 子句是非常有用的。

注释：并非所有的数据库系统都支持 TOP 子句。

**SQL Server 的语法：**

```sql
SELECT TOP number|percent column_name(s)
FROM table_name
```

**MySQL 语法**

```sql
SELECT column_name(s)
FROM table_name
LIMIT number
```

**Oracle 语法**

```sql
SELECT column_name(s)
FROM table_name
WHERE ROWNUM <= number
```

**SQL TOP PERCENT 实例**

上面的 "Persons" 表中选取 50% 的记录可以使用下面的 SELECT 语句：

```sql
SELECT TOP 50 PERCENT * FROM Persons
```



**2,LIKE 操作符**

LIKE 操作符用于在 WHERE 子句中搜索列中的指定模式。

语法:

```sql
SELECT column_name(s)
FROM table_name
WHERE column_name LIKE pattern
```

例1：

从 "Persons" 表中选取居住在以 "N" 开始的城市里的人：

我们可以使用下面的 SELECT 语句：

```sql
SELECT * FROM Persons
WHERE City LIKE 'N%'
```

提示："%" 可用于定义通配符（模式中缺少的字母）。

例2：

从 "Persons" 表中选取居住在以 "g" 结尾的城市里的人：

我们可以使用下面的 SELECT 语句：

```sql
SELECT * FROM Persons
WHERE City LIKE '%g'
```

例3：

从 "Persons" 表中选取居住在包含 "lon" 的城市里的人：

我们可以使用下面的 SELECT 语句：

```sql
SELECT * FROM Persons
WHERE City LIKE '%lon%'
```

例4：

通过使用 NOT 关键字，我们可以从 "Persons" 表中选取居住在*不包含* "lon" 的城市里的人：

我们可以使用下面的 SELECT 语句：

```sql
SELECT * FROM Persons
WHERE City NOT LIKE '%lon%'
```

