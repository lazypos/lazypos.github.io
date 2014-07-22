--------
layout: post
title: sql查询语句的关键语句点
------

**1、distinct (去重)**

语法: `select distinct filed from table`

注意：去重只能选择某一字段，不能多字段，结果集也只能有一个字段

**2、join (left join/right join/inner join/full join) （关联）**

描述：根据两个或多个表中，某些列之间的关系，查询数据

语法：`select 表.字段 from 表a  xxx join 表b on (关联的列a.field=b.field) where 其他条件`

注意：left join 返回左边表的所有行，即使右边没有匹配， right join 反之。full join 只要其中一个表存在就返回， join和inner join 同义

**3、union （union all）（合并）**

描述：合并两个或多个select语句返回的结果集 

语法：`select field from table1 union select field from table2`

注意：两个结果集必须有相同的列，字段类型。  返回的值如果有重复，默认会去重（所有字段都一样）， union all 不去重

**4、select into**

描述：选择数据插入到另一张表

语法：`select field into table2 from table1 （条件）`

**5、group by （分组/统计）**

描述：对多一个或多个结果列进行分组

语法：`select field， 函数 from table where （条件） group by field`

注意：一定要用一个合计函数，一般是count()/counts()或者 sum()

```
例子：统计个数表A中字段FIELD的不同值出现的次数
统计个数表A中字段FIELD的不同值出现的次数
select FIELD，count(FIELD) from  A group  by FIELD
```

**6、having**

描述：因为where后面的条件无法使用合计函数，所以要用having 代替

语法：`select field， 合计函数 from table where （条件） group by field having （合计函数的条件）`

注意：having一定要和group by一起使用，不能单独使用having

```
例子：统计个数表A中字段FIELD的不同值出现的次数 大于2次
select FIELD，count(FIELD) from  A group  by FIELD having count(FIELD) > 2
```




