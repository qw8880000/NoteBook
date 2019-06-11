# 最大连接数修改

show variables like '%max_connections%';

修改/etc/my.cnf 修改 max_connections=1000

# 修改密码

 alter user 'root'@'localhost' identified by '123';
