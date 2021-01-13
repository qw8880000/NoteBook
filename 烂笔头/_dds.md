
# dds文档

文档路径`SVN_13_运行三部\运维资料\软件安装\DDS`

# dds常用命令

源端：`vshms` `vs`
目标端：`vshmt` `vt`


源端：
```
su - dds
cd $DDS_DATA
ddstart              --启动软件
ddstop               --关闭软件
vshms -p             --查看软件进程
vshms -m             --查看软件同步用户配置
vshms –o             --查看同步对象
vshms -t             --查看软件同步目标端地址
vs                   --查看源端软件工作日志
dds_pweb -s          --启动web监控，在浏览器输入http://ip:8303
dds_pweb -q          --关闭监控
map_start            --发起数据同步命令，必须在目标端配置完成后执行此命令，执行后执行vs查看软件日志。
```

目标端：
```
su - dds
cd $dds_DATA
ddsstart              --启动软件
ddstop          --关闭软件
vshmt -c             --查看状态
vshmt -p             --查看软件进程
vt                   --查看源端软件工作日志
dds_pweb -t          --启动web监控，在浏览器输入http://ip:8304
dds_pweb -q          --关闭监控
```

# dds重新全同步

源端：
* ddstop
* ddclean
* ddstart
* map_start

目标端：
* ddstop
* ddclean
* ddstart
