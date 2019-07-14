## 分区类型
### 一、按哈希分区(Hash)

### 二、按范围分区(Range)
#### Range 分区的特点
- 根据分区键值的范围把数据行存储到表不同的分区中
- 多个分区的范围要连续，但不能重叠
- 默认情况下使用 VALUES LESS THAN 属性，即每个分区不包括指定的那个值

#### 适用场景
- 分区键为日期或者时间
- 所有查询中都包括分区键
- 定期按范围清理历史数据

例子：<br >
```mysql
CREATE TABLE `user_login_log` (
    id INT(10) UNSIGNED NOT NULL,
    login_time TIMESTAMP NOT NULL,
    login_ip INT(10) UNSIGNED NOT NULL
) ENGINE = INNODB
PARTITION BY RANGE (id) (
    PARTITION p0 VALUES LESS THAN (100000),
    PARTITION p1 VALUES LESS THAN (200000),
    PARTITION p2 VALUES LESS THAN (300000),
    PARTITION p3 VALUES LESS THAN MAXVALUE
);
```
### 三、List 分区
#### List 分区的特点
- 按分区键取值的列表进行分区

例子：<br >
```mysql
CREATE TABLE `user_login_log_list` (
    id INT(10) UNSIGNED NOT NULL,
    login_time TIMESTAMP NOT NULL,
    login_ip INT(10) UNSIGNED NOT NULL,
    login_type TINYINT(1) NOT NULL
) ENGINE = INNODB
PARTITION BY LIST (login_type) (
    PARTITION p0 VALUES IN (1,3,5,7,9),
    PARTITION p1 VALUES IN (2,4,6,8)
);
```

## 注意事项
- 结合业务场景选择分区键，避免跨分区查询
- 对分区表查询，最好在 where 条件中包含分区键
- 具有主键或者唯一索引的表，主键或唯一索引必须是分区键的一部分