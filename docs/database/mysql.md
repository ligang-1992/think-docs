#### 多表查询修改

```
update tableA a
left join tableB b on
    a.name_a = b.name_b
set
    validation_check = if(start_dts > end_dts, 'VALID', ''
```

#### 基本操作

```
/* windows 服务 */
-- 启动mysql
	net start mysql
-- 创建windows服务
	sc create mysql binPath = mysql_bin_path(注意：等号与值之间有空格)
/* 链接与断开服务器 */
mysql -h 地址 -p 端口 -u 用户名 -p 密码
SHOW PROCESSLIST -- 显示哪些线程正在运行
SHOW VARIABLES -- 显示系统变量信息
```

#### 数据库操作

```
/* 数据库操作 */
-- 查看当前数据库
	select database();
-- 显示当前时间、用户名、数据库版本
	select now(), user(), version();
-- 创建库
	create database[if not exists] 数据库名 数据库选项	
        数据库选项：
            CHARACTER SET charset_name
            COLLATE collation_name
-- 查看已有库
    SHOW DATABASES[ LIKE 'PATTERN']
-- 查看当前库信息
    SHOW CREATE DATABASE 数据库名
-- 修改库的选项信息
    ALTER DATABASE 库名 选项信息
-- 删除库
    DROP DATABASE[ IF EXISTS] 数据库名       
		同时删除该数据库相关的目录及其目录内容
```

#### 表的操作
