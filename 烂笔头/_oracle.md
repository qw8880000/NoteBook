## 启停

- 启动

1. sqlplus / as sysdba，然后执行startup命令
1. 一般监听会自动启动，查看一下lsnrctl status

- 关闭

1. sqlplus / as sysdba，然后执行shutdown immediate命令

- 监听相关命令

1. 执行lsnrctl start 启动监听
1. 执行lsnrctl stop 关闭监听

## 查看oracle视图表结构


select * from user_tab_columns where TABLE_NAME='视图名'

## 查看临时表空间

用下面语句可查看当前临时表空间使用空间大小与正在占用临时表空间的sql语句：

select sess.SID, segtype, blocks * 8 / 1000 "MB", sql_text
  from v$sort_usage sort, v$session sess, v$sql sql
 where sort.SESSION_ADDR = sess.SADDR
   and sql.ADDRESS = sess.SQL_ADDRESS
 order by blocks desc;

下面语句查询临时表空间的空闲程度：

select 'the ' || name || ' temp tablespaces ' || tablespace_name ||
       ' idle ' ||
       round(100 - (s.tot_used_blocks / s.total_blocks) * 100, 3) ||
       '% at ' || to_char(sysdate, 'yyyymmddhh24miss')
  from (select d.tablespace_name tablespace_name,
               nvl(sum(used_blocks), 0) tot_used_blocks,
               sum(blocks) total_blocks
          from v$sort_segment v, dba_temp_files d
         where d.tablespace_name = v.tablespace_name(+)
         group by d.tablespace_name) s,
       v$database;



## 查看触发器内容

```
一.查all_triggers表得到trigger_name

select trigger_name from all_triggers where table_name='XXX';  

二.根据trigger_name查询出触发器详细信息

select text from all_source where type='TRIGGER' AND name='TR_XXX';

```

## 表空间查看

```
select t.* from (
              SELECT D.TABLESPACE_NAME,
                     SPACE "SUM_SPACE(M)",
                     BLOCKS SUM_BLOCKS,
                     SPACE-NVL(FREE_SPACE,0) "USED_SPACE(M)",
                     ROUND((1-NVL(FREE_SPACE,0)/SPACE)*100,2) "USED_RATE(%)",
                     FREE_SPACE "FREE_SPACE(M)"
                FROM (SELECT TABLESPACE_NAME,
                             ROUND(SUM(BYTES)/(1024*1024),2) SPACE,
                             SUM(BLOCKS) BLOCKS
                        FROM DBA_DATA_FILES
                      GROUP BY TABLESPACE_NAME) D,
                     (SELECT TABLESPACE_NAME,
                             ROUND(SUM(BYTES)/(1024*1024),2) FREE_SPACE
                        FROM DBA_FREE_SPACE
                       GROUP BY TABLESPACE_NAME) F
                WHERE  D.TABLESPACE_NAME = F.TABLESPACE_NAME(+)
              UNION ALL  --if have tempfile
               SELECT D.TABLESPACE_NAME,
                     SPACE "SUM_SPACE(M)",
                     BLOCKS SUM_BLOCKS,
                     NVL(USED_SPACE, 0) "USED_SPACE(M)",
                     ROUND(NVL(USED_SPACE, 0)/NVL(SPACE, 0) * 100, 2) "USED_RATE(%)",
                     NVL(D.SPACE, 0) - NVL(F.USED_SPACE, 0) "FREE_SPACE(M)"
                 FROM (SELECT TABLESPACE_NAME,
                            NVL(ROUND(SUM(BYTES)/(1024*1024), 2), 0) SPACE,
                            SUM(BLOCKS) BLOCKS
                       FROM DBA_TEMP_FILES
                      GROUP BY TABLESPACE_NAME) D,
                    (SELECT TABLESPACE,
                            NVL(ROUND(SUM(BLOCKS*8192)/(1024*1024), 2), 0) USED_SPACE
                       FROM V$SORT_USAGE
                     GROUP BY TABLESPACE) F
              WHERE  D.TABLESPACE_NAME = F.TABLESPACE(+)       
    ) t
  order by "USED_RATE(%)" desc;
```

## 数据字典

数据字典记录了数据库的系统信息，它是只读表和视图的集合，数据字典的所有者为sys用户。
数据字典视图主要包括user_xxx，all_xxx，dba_xxx三种类型。

http://www.hechaku.com/Oracle/oracle_liber_pic.html

* 查看所有的数据字典视图：select * from all_views t

## 查看dds同步部署是否需要重启主库
```
set linesize 333
col name for a35
col description for a66
col value for a30
SELECT   i.ksppinm name,  
   i.ksppdesc description,  
   CV.ksppstvl VALUE
FROM   sys.x$ksppi i, sys.x$ksppcv CV  
   WHERE   i.inst_id = USERENV ('Instance')  
   AND CV.inst_id = USERENV ('Instance')  
   AND i.indx = CV.indx  
   AND i.ksppinm LIKE '/_log_parallelism%' ESCAPE '/'  
ORDER BY   REPLACE (i.ksppinm, '_', '');
```
如果 `_log_parallelism_dynamic` 为true 且 `_log_parallelism_dynamic` 为 1则不需要重启主库

## pl/sql developer

PLSQL Developer 攻略:https://www.cnblogs.com/mq0036/p/6437834.html

## sqlplus

  - sqlplus /nolog : 选项可启动 SQL*Plus 而不连接到数据库
  - conn sys/sysinitpwd as sysdba

## expdp
https://www.jianshu.com/p/923b2fa2643f

* 按表导出
  expdp system/oracle dumpfile=test.dmp DIRECTORY=DUMP_TEST TABLES=testuser.student;

* 导出时覆盖原有的文件
  expdp system/oracle dumpfile=test.dmp DIRECTORY=DUMP_TEST REUSE_DUMPFILES=y schemas=testuser;

* 导出多个用户
  expdp system/oracle dumpfile=test.dmp DIRECTORY=DUMP_TEST schemas=testuser,testuser1;

* exclude 排除多个文件
  expdp system/oracle dumpfile=test.dmp DIRECTORY=DUMP_TEST schemas=testuser,testuser1 EXCLUDE=TABLE:\"like \'%ENT1\'\" EXCLUDE=TABLE:\"like \'%ENT2\'\";

## 使用expdp备份数据

1. 查看当前数据库存在的directory路径:

```
SQL> select * from dba_directories;
```

1. 创建自定义的导出导入路径：
```
[oracle@testdb ~]$ mkdir /oradata/datapump

SQL> CREATE DIRECTORY datapump AS '/oradata/datapump';
```

1. 给用户授权
```
GRANT READ,WRITE ON DIRECTORY datapump TO User1;
GRANT EXP_FULL_DATABASE,RESOURCE,CONNECT TO User1;
```

1. 按用户导出
编辑expdp_user1.par文件
```
userid="/ as sysdba"
directory=datapump
job_name=job_expdp_user1
dumpfile=expdp_user1%u.dmp
logfile=expdp_user1.log
cluster=n
schemas=(
user1
)
parallel=4
filesize=500m
COMPRESSION=all
```

执行导出
```
nohup expdp parfile=expdp_user1.par &
```

1. 按用户表（TABLE）
编辑expdp_user1.par文件
```
userid="/ as sysdba"
directory=datapump
dumpfile=expdp_user1%u.dmp
logfile=expdp_user1.log                                                     
cluster=n
tables=(
user1.t1
user1.t2
user2.t3
user2.t4
)
parallel=4
```

执行导出
```
nohup expdp parfile=expdp_user1.par &
```

1. 按整库（DATABASE）
编辑expdp_user1.par文件
```
userid="/ as sysdba"
directory=datapump
job_name=job_expdp_user1
dumpfile=expdp_full%u.dmp
logfile=expdp_full.log                                                     
cluster=n
full=y
parallel=4
filesize=500m
```

执行导出
```
nohup expdp parfile=expdp_user1.par &
```

## expdp parfile参数介绍
```
首先，强烈建议使用parfile参数,将需要用到的参数整合到一个par文件中，不止美观，也可以留下记录。

userid          -- 账号密码
directory       -- 指定数据泵的目录路径，生成的dmp文件也在该目录下
job_name     -- 数据泵任务的名称,因为是sys用户，所以名称为"SYS"."JOB_EXPDP_USER1"
dumpfile       -- dmp文件的名称,使用并行导出到多个文件，需要用到%u
logfile           -- 记录整个导出过程的日志文件
cluster          -- RAC集群必须指定为N,否则数据库不知道从哪个实例导出，会报错
schema         -- 指定要导出的用户名
parallel   -- 并行度，取决服务器的cpu个数,生产繁忙时不要导出大数据量
filesize   -- 指定每个dmp文件的大小，不指定，dmp文件的大小会不统一。
COMPRESSION=all   -- 是否要进行压缩，压缩比率为1:7左右，本地磁盘空间不足或需要跨网络传输时，建议压缩，否则不建议，会消耗服务器一些性能，降低了导出导入的效率。
```

注意，当密码中包含@符号时，需要转义，不然会报错“ORA-12154: TNS:could not resolve the connect identifier specified”
直接这样写会报错  USERID=tibco/abc@123 ，这样写也会报错 USERID="tibco/abc@123"
改成这样 USERID=tibco/"abc@123" 可以

## impdp
1. 按用户导入
编辑para.par文件
```
userid="/ as sysdba"
directory=datapump
dumpfile=expdp_user1%u.dmp
logfile=impdp_user1.log                                                     
cluster=n
remap_schemas=user1:user3
parallel=4
remap_tablespace=tbs1:tbs3
table_exists_action=replace
```
执行导入
```
impdp parfile=para.par
```

参数介绍
```
dumpfile --名称为源库导出的dmp文件名
remap_schemas --将源库的user1用户数据迁移 -- > 目标库的user3用户
remap_tablespace --指定源库tbs1表空间的数据 --> 目标库的表空间tbs3
table_exists_action -- replace替换, 目标导入库的用户存在相同表名，会替换掉(drop），truncate（存在表truncate），append(追加数据)
```

1. 按表导入
编辑para.par文件
```
userid="/ as sysdba"
directory=DATAPUMP
dumpfile=expdp_tablename_20160510_%u.dmp
logfile=imppdp_tablename_20160510_.log
remap_schema=(User1:User2)
remap_tablespace=
(
source_tbs1:des_tbs1
source_index1:des_index1
)
tables=(
user1.Tablename1
user1.Tablename2
)
CLUSTER=N
remap_table=(
Tablename1:Tbname2
Tablename2:Tbname2)
table_exists_action=truncate
parallel=4
```

执行导入
```
impdp parfile=para.par
```



1. 导入整库

导入数据库

```
impdp system/redhat directory=dump_scott dumpfile=full.dmp full=y  
```





## 查询分区表

select table_owner,table_name,partition_name from dba_tab_partitions where table_owner not like '%SYS%';

## 跟踪日志

$ORACLE_BASE/diag/rdbms/esbdb/esbdb/trace/esbdb_lgwr_xxxxx.trc

## 设置oracle开机启动

自动启动Oracle
1、root用户修改oratab
$ vi /etc/oratab
文件尾部的N改为Y：
orcl:/u01/app/oracle/product/11.2.0/db_1:Y 
2、root用户修改
$ vi /etc/rc.local
在文件尾部添加：
su - oracle -c "dbstart"; su - oracle -c "lsnrctl start"

## oracle常用

查看表的大小:`select segment_name,bytes/1024/1024||'MB' from dba_segments where owner='ITSM_XYZQ' and SEGMENT_TYPE='TABLE' order by bytes desc;`

查看用户下有哪些表:
select table_name from user_tables; //当前用户拥有的表       
select table_name from all_tables; //所有用户的表
select table_name from dba_tables; //包括系统表
select table_name from dba_tables where owner='用户名'

查看注释:
select * from dba_tab_comments where owner='ITSM_XYZQ' and table_type='TABLE';

查看表字段：

```
select a.*,b.*,c.bytes/1024/1024||'MB' size from dba_tab_comments a
left join dba_col_comments b
on a.table_Name=b.table_Name
left join dba_segments c
on a.table_name=c.segment_name
where a.table_type='TABLE' and a.owner='ITSM_XYZQ'
order by a.table_name
```

查看注释与大小：

```
select a.table_name,a.comments,b.bytes/1024/1024||'MB' size from dba_tab_comments a
left join dba_segments b
on a.table_name=b.segment_name
where a.table_type='TABLE' and a.owner='ITSM_XYZQ' order by a.table_name;
```

字符串截取(substr与instr函数)：

```
select SUBSTR(SVCOPNAME,1,INSTR(SVCOPNAME,'-',1,1)-1) AS server,SUBSTR(SVCOPNAME,INSTR(SVCOPNAME,'-',1,1)+2) AS oper,ALLOWEDUSERS from ESB_ACL t;
```

## 查看某个表授权给哪些用户

SELECT * FROM user_tab_privs t 
where t.TABLE_NAME=upper('表名'); 

SELECT * FROM dba_tab_privs t 
where t.TABLE_NAME=upper('表名'); 

## 授权查询



