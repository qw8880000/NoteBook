
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
