# 执行计划中的内容

### id
id 列中的数据为一组数字，表示执行 select 语句的顺序 <br />
id 值相同时，执行顺序由上至下 <br />
id 值越大优先级越高，越先被执行

### select_type
value              | 含义
------------------ | ----------------------------
SIMPLE             | 不包含子查询或是 UNION 操作的查询
PRIMARY            | 包含子查询
SUBQUERY           | SELECT 列表中的子查询
DEPENDENT SUBQUERY | 以来外部结果的子查询
UNION              | 111
DEPENDENT UNION    | 当 UNION 作为子查询时
UNION RESULT       | UNION 产生的结果集
DERIVED            | 出现在 FROM 子句中的子查询

### table
输出数据行所在的表的名称 <br />
`<unionM,N>` 由 ID 为 M，N 查询union产生的结果集 <br />
`<derivedN>` / `<subqueryN>` 由 ID 为 N 的查询产生的结果

### partitions 
显示查询的分区id

### type
连接类型

value       | 含义
----------- | -------
system      | 查询的表只有一行数据时
const       | 有且只有一个匹配的行，如对主键或唯一索引的查询
eq_ref      | 唯一索引或主键查找，对于每个索引键，表中只有一条记录匹配(join查询)
ref         | 非唯一索引查找，返回匹配某个单独值的所有行
ref_or_null | 类似于ref类型查询，但是附加了对 NULL 值列的查询
index_merge | 表示使用了索引合并优化方法
range       | 索引范围扫描，常见于 `between`、`>` 这样的查询条件
index       | full index scan全索引扫描，和 all的区别是，遍历的是索引树
all         | 全表扫描

### possiable_keys
指出mysql能使用哪些索引来优化查询 <br />
查询列所涉及到的列上的索引都会被列出来，单不一定会被使用 <br />

### key
实际使用的索引

### key_len 
表示索引字段的最大可能长度

### ref
表示哪些列或常量被用于查找索引列上的值

### rows
表示mysql通过索引统计信息，估算的所需读取的行数

### filtered
表示返回结果的行数占需读取行数的百分比

### Extra
附加信息

value           | 含义
--------------- | --------------------------------
distinct        | 优化操作，找到第一匹配的元组后停止找同样值的操作
not exists      | 使用 not exists 来优化查询
using filesort  | 使用额外操作进行排序，通常会出现在order by 或 group by 中
using index     | 使用了覆盖索引进行查询
using temporary | mysql使用临时表处理查询，常见于排序、子查询、分组查询
using where     | 需要在mysql服务器层使用where条件来过滤数据
select tables optimized away | 直接通过索引来获得数据，不用访问表
