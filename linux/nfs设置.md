@Filename:       2.6.4 nfs设置.md
@Author:         wangjl
@Date:           2015-10-12 16:21
@Last modified:   2015-10-12 16:21
@Description:   

#### 设置开发板ip地址

    ifconfig eth0 192.168.60.205

#### 测试与主机是否连通

    ping 192.168.60.213  (主机)

#### 开启主机的NFS服务器

* 安装nfs服务器：

    sudo apt-get install nfs-kernel-server

* 关闭防火墙：

    ufw disable

* 设置共享目录

    $ vim /etc/exports  
    添加以下内容：  
    /opt/FriendlyARM/mini6410/linux/ *(rw,sync,no_root_squash)，表示将要共享这个目录。

    "*" 表示所有的客户机都可以挂接此目录  
    rw 表示挂接此目录的客户机对该目录有读写的权力  
    no_root_squash 表示允许挂接此目录的客户机享有该主机的 root 身份  
    
* 启动NFS服务：
    /etc/init.d/nfs-kernel-server start
* 查看NFS运行情况：
    /etc/init.d/nfs-kernel-server status
* 查看共享出的目录
    showmount -e  
    如果显示的目录与我们设置的目录一致，则正确。

* 测试是否设置成功：
    在本机上试一下：   
    mount -t nfs localhost:/opt/FriendlyARM/mini6410/linux/ /mnt/   
    然后查看/mnt 目录，如果与/opt/FriendlyARM/mini6410/linux/目录下的内容一致，则设置挂载成功。

* 取消挂载：
    umount /mnt

#### 客户端NFS设置

* 内核配置
    File systems  --->  
        [*] Network File Systems  --->  
            <*>   NFS client support  
            [*]     NFS client support for NFS version 3    
            [*]       NFS client support for the NFSv3 ACL protocol extension   
            [*]     NFS client support for NFS version 4    
            [*]       NFS client support for NFSv4.1 (EXPERIMENTAL)   

* 挂载方法
    mount -t nfs -o nolock 192.168.60.213:/opt/FriendlyARM/mini6410/linux/ /mnt/ 

### 常见问题

##### 客户端mount时，提示 failed: No such device

    原因：不支持NFS文件系统
    解决：参考客户端NFS配置
