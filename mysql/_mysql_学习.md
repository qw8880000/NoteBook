
《数据库系统概念》
《数据库系统概论》
《轻松掌握SQL》

https://zhuanlan.zhihu.com/p/31786056



mysql学习:http://www.notedeep.com/note/38/page/282
    《mysql必知必会》《高性能mysql第三版》《数据库系统概念》《深入理解MySQL》《MySQL性能调优与架构设计--全册》《SQL Antipatterns》《MySQL技术内幕 InnoDB存储引擎》



# 行转列

'''sql

SELECT 
	substring_index( substring_index( a.field, ',', b.help_topic_id + 1 ), ',',- 1 ) 
FROM (
select '192.168.1.1,192.168.1.2' as field ) a
	CROSS JOIN mysql.help_topic b ON b.help_topic_id < ( length( a.field ) - length( REPLACE ( a.field, ',', '' ) ) + 1 )

'''

