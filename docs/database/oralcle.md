##### 5、删除表名为小写字母的表

```
drop table "table_name"
```



##### 4、SQL SELECT DISTINCT 语句

在表中，可能会包含重复值。这并不成问题，不过，有时您也许希望仅仅列出不同（distinct）的值。

关键词 DISTINCT 用于返回唯一不同的值。

###### 语法：

```sql
SELECT DISTINCT 列名称 FROM 表名称
```

###### 注意：

```
DISTINCT 的使用是基于列出来的所有列了，假如查询的语句只列出一个字段，则以为这个字段去除重复，假如列出多个字段，则以列出的这些字段来去除重复
```

##### 3、oracle 排序问题

```
假如排序字段的值一致，排序就会失去作用，数据顺序混乱
```

##### 2、动态累加

```
select 列名,sum(需要累加的列名) over(order by 列名) as 别名 from 表名 order by 列名；

select 列名,sum(需要累加的列名) over(partition by 列名 order by 列名) as 别名 
	from 表名 order by 列名；

```

##### 1、精确小数点后两位

```
1、ROUND(number，2)
2、CAST(expression AS data_type) 例如：CAST(12.2333 AS number(10, 2)) 
	10:精度
	2:显示有效小数位
```

