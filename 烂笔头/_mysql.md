# mysql 教程

- [mysql教程 - begtut.com](https://www.begtut.com/mysql/mysql-tutorial.html)

# 最大连接数修改

show variables like '%max_connections%';

修改/etc/my.cnf 修改 max_connections=1000

# 修改密码

 alter user 'root'@'localhost' identified by '123';

# 查看用户权限

* `show grants for user`
* `select * from mysql.user where user = 'user'`

# 一行转多行

```sql
SELECT
 substring_index(substring_index('1,2,3,4',',', b.help_topic_id + 1), ',', -1) result
FROM
 mysql.help_topic b
where
 b.help_topic_id <  (LENGTH('1,2,3,4') - LENGTH(REPLACE('1,2,3,4', ',', '')) + 1);
```