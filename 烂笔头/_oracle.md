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

* 覆盖导出文件
expdp system/oracle dumpfile=test.dmp DIRECTORY=DUMP_TEST REUSE_DUMPFILES=y schemas=testuser;

* 导出多个用户
expdp system/oracle dumpfile=test.dmp DIRECTORY=DUMP_TEST schemas=testuser,testuser1;

* exclude 排除多个文件
expdp system/oracle dumpfile=test.dmp DIRECTORY=DUMP_TEST schemas=testuser,testuser1 EXCLUDE=TABLE:\"like \'%ENT1\'\" EXCLUDE=TABLE:\"like \'%ENT2\'\";

* 导入文件
impdp system/oracle dumpfile=test.dmp DIRECTORY=DUMP_TEST;

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