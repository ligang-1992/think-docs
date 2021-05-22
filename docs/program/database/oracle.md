#### Oracle Database

##### 安装

###### 步骤一：拉取镜像

```shell
# 拉取image：
~ % docker pull store/oracle/database-enterprise:12.2.0.1
```

###### 步骤二：创建容器

```shell
# 第一种创建oracle容器的方法：
~ % docker login
~ % docker run -d -it --name dev-oracle -p 1521:1521 -p 5500:5500  -v $PWD/devtools/docker/oracle/data:/ORCL --env-file $PWD/devtools/docker/oracle/env/env.dat store/oracle/database-enterprise:12.2.0.1

# 第二种创建oracle容器的方法(已经连接成功)：
~ % docker login
~ % docker run -d -it --name dev-oracle -p 1521:1521 -p 5500:5500 -v $PWD/devtools/docker/oracle/data:/ORCL store/oracle/database-enterprise:12.2.0.1

# oracle 默认密码： Oradoc_db1
```

###### 步骤三：进入容器创建存放表空间文件的文件夹

```shell
# 进入oracle容器的方法
# 进入容器并连接数据库
~ % docker exec -it dev-oracle bash -c "source /home/oracle/.bashrc; sqlplus /nolog"
# ~ % sqlplus sys/Oradoc_db1@ORCLCDB as sysdba
# 以root权限进入容器
~ % docker exec -it --user root dev-oracle /bin/bash
~ % docker exec -it --user oracle dev-oracle /bin/bash

# 创建表空间存放路径
[root@a3b2f1adcd02 /]# mkdir -p /home/oracle/data/retail
# 给oracle用户赋权，以便创建表空间文件
[root@a3b2f1adcd02 /]# chown -R oracle:oinstall /home/oracle/data/retail/

# 配置环境
[root@5b410880417d /]# vi /etc/profile
# 加在配置文件最后
export ORACLE_HOME=/home/oracle/app/oracle/product/12.2.0.1/dbhome_2
export ORACLE_SID=ORCLCDB
export PATH=$ORACLE_HOME/bin:$PATH
# 软件连接
[root@a3b2f1adcd02 /]#  ln -s $ORACLE_HOME/bin/sqlplus /usr/bin
```

###### 步骤四：创建表空间以及用户

```sql
# 连接数据库
SQL> conn / as sysdba;
# 修改用户密码
SQL> alter user system identified by 123456;
SQL> alter user sys identified by 123456;
SQL> ALTER PROFILE DEFAULT LIMIT PASSWORD_LIFE_TIME UNLIMITED;

# 查看所有表空间
SQL> select tablespace_name,status,contents from user_tablespaces; 
SQL> alter session set container=cdb$root;

SQL> alter session set container=ORCLPDB1;

# 创建表空间
SQL> create tablespace retail datafile '/u02/app/oracle/oradata/ORCL/temp02.dbf'  size 200M autoextend on next 50M;
SQL> create tablespace retail datafile '/home/oracle/data/cdb/retail.dbf' size 200M autoextend on next 50M;
SQL> create tablespace retail datafile '/home/oracle/data/pdb/retail.dbf' size 200M autoextend on next 50M;

SQL> create tablespace retail datafile '/home/oracle/data/retail/retail.dbf' size 10M autoextend on maxsize 1G;

# 在表空间上创建用户
create user c##retail identified by 123456 default tablespace RETAIL temporary tablespace TEMP;
# 第一种创建用户的方法
SQL> create user retail identified by 123456 default tablespace retail;
# 第二种创建用户的方法 cdb下
SQL> create user c##retail identified by 123456 default tablespace retail;

# 修改密码
SQL> alter user retail identified by 123456;

# 删除用户
SQL> DROP USER retail CASCADE;

# 给新建的用户赋权
SQL> grant connect,resource,dba to C##RETAIL;

# delete tablespace
SQL> drop tablespace retail including contents and datafiles

-- 1 查看系统中的容器：
--    select con_id,dbid,NAME,OPEN_MODE from v$pdbs;
-- 2 先打开pdb容器：
--    alter pluggable database ORCLPDB1 open;
-- 3再查看容器，pdb应该是READ，WRITE：
--    select con_id,dbid,NAME,OPEN_MODE from v$pdbs;
-- 4切换容器：
--    alter session set container=ORCLPDB1;
-- 5查看当前使用的容器
--    select sys_context ('USERENV', 'CON_NAME') from dual;
-- create tablespace retail 
-- datafile '/u02/app/oracle/oradata/ORCL/retail.dbf' 
-- size 50M 
-- autoextend on next 50m maxsize 2048m 
-- extent management local;
-- 
-- create temporary tablespace retail_temp
-- tempfile '/u02/app/oracle/oradata/ORCL/retail_temp.dbf'
-- size 32m
-- autoextend on next 32m maxsize 1024m
-- extent management local;

create user henfengyu identified by 123456 default tablespace retail
temporary tablespace retail_temp;

grant connect,resource to henfengyu;
grant dba to henfengyu;

alter user henfengyu account unlock identified by 123456;
```

更新时间：2020-03-21



##### 查看表结构修改记录

```sql
# 修改项目时，涉及到了Oracle中许多表的修改（包括：增加、删除字段，修改注释等）。由于开始没有进行记录，造成在上测试机时，忘记了具体修改过哪些表了。后来在网上查找了一些资料，例如：

# 该SQL可以获得所有用户表的名称
SQL> select uat.table_name from user_all_tables uat 
    
# 该SQL可以获得所有用户对象（包括表）的创建和最后修改时间
SQL> select object_name, created,last_ddl_time from user_objects 
    
#综合以上SQL，总结了如下语句：
SQL> select uat.table_name as 表名,(select last_ddl_time from user_objects where object_name = uat.table_name ) as 最后修改日期 from user_all_tables uat

# 通过该语句，可以得到所有表的最后修改时间。（大家可以根据实际情况在该SQL后面加上相应的条件表达式）
# 通过对查询结果中最后修改时间的降序排列，就可以知道那些表的结构修改过了。
```



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

##### 查询数据库所有表明

```sql
select t.table_name, t.num_rows from user_tables t;
```

