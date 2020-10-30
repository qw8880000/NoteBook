# 全量备份步骤

* 主库完全备份
  - innobackupex --defaults-file=/etc/my.cnf --user=root --password=123123 /backup/xyzq
* 将备份拷贝至备机上
* 还原数据前的"准备"工作 - 事务日志应用到备份
  - innobackupex --apply-log /backup/xyzq
* 先停止数据库服务，且对应的数据目录为空
  - 停备库
  - mv data/ data_bak/
  - mkdir data/
* 恢复数据
  - innobackupex --defaults-file=/etc/my.cnf --copy-back --rsync /data/xyzq
  - --datadir：指定的目录就是还原后数据要存放的目录，如果my.cnf设置了datadir，可以省略--datadir
  - --copy-back：对应的目录就是我们准备好的可用数据的目录
* 确认data目录的属组
  - chown 属组为 mysql:mysql
* 启动备库
  - 启动备库
  - 开启主从同步：change master to master_host='xyzq-nn1.xysec.com',master_user='repl',master_password='123',master_log_file='mysqlmaster-bin.000002',master_log_pos=193482964;

# 参考

* https://www.cnblogs.com/waynechou/p/xtrabackup_backup.html
* https://blog.csdn.net/fanren224/article/details/79693863
