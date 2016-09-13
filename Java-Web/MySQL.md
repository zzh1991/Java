##MySQL

###登入MySQL
* mysql -h 127.0.0.1 -u 用户名 -p
* mysql -D 所选择的数据库名 -h 主机名 -u 用户名 -p

###创建数据库
```SQL
-- 创建一个名为 samp_db 的数据库，数据库字符编码指定为 utf-8
create database samp_db character set utf-8;
drop database samp_db; -- 删除 库名为samp_db的库
show databases;        -- 显示数据库列表。
use samp_db;    -- 选择创建的数据库samp_db
show tables;       -- 显示samp_db下面所有的表名字
describe 表名;   -- 显示数据表的结构
delete from 表名; -- 清空表中记录
```

###创建数据库表
```SQL
CREATE TABLE `user_accounts` (
  `id`             int(100) unsigned NOT NULL AUTO_INCREMENT primary key,
  `password`       varchar(32)       NOT NULL DEFAULT '' COMMENT '用户密码',
  `reset_password` tinyint(32)       NOT NULL DEFAULT 0 COMMENT '用户类型：0－不需要重置密码；1-需要重置密码',
  `mobile`         varchar(20)       NOT NULL DEFAULT '' COMMENT '手机',
  `create_at`      timestamp(6)      NOT NULL DEFAULT CURRENT_TIMESTAMP(6),
  `update_at`      timestamp(6)      NOT NULL DEFAULT CURRENT_TIMESTAMP(6) ON UPDATE CURRENT_TIMESTAMP(6),
  -- 创建唯一索引，不允许重复
  UNIQUE INDEX idx_user_mobile(`mobile`)
)
ENGINE=InnoDB DEFAULT CHARSET=utf8
COMMENT='用户表信息';
```

###常规操作
* 增删改查
* where
* and、or
* ORDER BY（DESC - 按照降序对记录进行排序；ASC - 按照升序对记录进行排序）
* in
* not
* as
* join
    * JOIN: 如果表中有至少一个匹配，则返回行
    * INNER JOIN: 在表中存在至少一个匹配时，INNER JOIN 关键字返回行
    * LEFT JOIN: 即使右表中没有匹配，也从左表返回所有的行
    * RIGHT JOIN: 即使左表中没有匹配，也从右表返回所有的行
    * FULL JOIN: 只要其中一个表中存在匹配，就返回行
* SQL函数：count、max、min、aver

###创建索引
```SQL
-- –直接创建索引
CREATE INDEX index_user ON user(title)
-- –修改表结构的方式添加索引
ALTER TABLE table_name ADD INDEX index_name ON (column(length))
-- 给 user 表中的 name字段 添加普通索引(INDEX)
ALTER TABLE `table` ADD INDEX index_name (name)
-- –创建表的时候同时创建索引
CREATE TABLE `table` (
    `id` int(11) NOT NULL AUTO_INCREMENT ,
    `title` char(255) CHARACTER SET utf8 COLLATE utf8_general_ci NOT NULL ,
    `content` text CHARACTER SET utf8 COLLATE utf8_general_ci NULL ,
    `time` int(10) NULL DEFAULT NULL ,
    PRIMARY KEY (`id`),
    INDEX index_name (title(length))
)
-- –删除索引
DROP INDEX index_name ON table
```

###主键索引
```SQL
-- 给 user 表中的 id字段 添加主键索引(PRIMARY key)
ALTER TABLE `user` ADD PRIMARY key (id);
```

###唯一索引
```SQL
-- 给 user 表中的 creattime 字段添加唯一索引(UNIQUE)
ALTER TABLE `user` ADD UNIQUE (creattime);
```

###全文索引
```SQL
-- 给 user 表中的 description 字段添加全文索引(FULLTEXT)
ALTER TABLE `user` ADD FULLTEXT (description);
```

###多列索引
```SQL
-- 给 user 表中的 name、city、age 字段添加名字为name_city_age的普通索引(INDEX)
ALTER TABLE user ADD INDEX name_city_age (name(10),city,age); 
在LIKE以通配符%和_开头作查询时，MySQL不会使用索引
```

##创建表后的修改
###添加列
```SQL
-- 在表students的最后追加列 address: 
alter table students add address char(60);
-- 在名为 age 的列后插入列 birthday: 
alter table students add birthday date after age;
```

###修改列
```SQL
-- 将表 tel 列改名为 telphone: 
alter table students change tel telphone char(13) default "-";
-- 将 name 列的数据类型改为 char(16): 
alter table students change name name char(16) not null;
```

###删除列
```SQL
-- 删除表students中的 birthday 列: 
alter table students drop birthday;
```

###重命名表
```SQL
-- 重命名 students 表为 workmates: 
alter table students rename workmates;
```

###清空表数据
```SQL
-- 清空表为 workmates 里面的数据，不删除表。 
delete from workmates;
```

###删除整张表
```SQL
-- 删除 workmates 表: 
drop table workmates;
```
