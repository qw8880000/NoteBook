windows下的git客户端使用git status的时候中文显示是乱码的：
![image](http://qiniu.wangjinle.com/git_status_%E4%B8%AD%E6%96%87%E4%B9%B1%E7%A0%81_1.png)

修改了以下两个配置后解决：

1. 修改客户端的character set为utf-8编码
![image](http://qiniu.wangjinle.com/git_status_%E4%B8%AD%E6%96%87%E4%B9%B1%E7%A0%81_2.png)

2. 执行以下命令
`git config --global core.quotepath false`
