
# 参考资料

* [Docker 入门教程 - 阮一峰](http://www.ruanyifeng.com/blog/2018/02/docker-tutorial.html)
* [Docker 从入门到实践 国内镜像](https://gitee.com/docker_practice/docker_practice)

# docker 在 RHEL 下如何安装

参考教程：[Get Docker EE for Red Hat Enterprise Linux](https://docs.docker.com/install/linux/docker-ee/rhel/#install-from-the-repository)

安装中有个问题，就是提示`container-selinux >= 2.9`，具体解决是：
  - 查看系统中是否有基本的yum源，没有的话加入源。（例如：http://mirrors.aliyun.com/repo/Centos-7.repo）
  - yum中加入 epel 源（例如：`http://mirrors.aliyun.com/repo/epel-7.repo`）
  - `yum-config-manager --enable rhel-7-server-extras-rpms`

如果执行`yum-config-manager --add-repo "$DOCKERURL/rhel/docker-ee.repo"`失败，可以手动下载这个repo文件，然后放到`/etc/yum.repos.d/` 下面。

# docker 仓库

* [Docker Hub](https://hub.docker.com/)
* [镜像加速 | docker 中国](https://www.docker-cn.com/registry-mirror)

# CentOS/RHEL 的用户需要注意的事项

在 Ubuntu/Debian 上有 UnionFS 可以使用，如 aufs 或者 overlay2 ，而 CentOS 和 RHEL
的内核中没有相关驱动。因此对于这类系统，一般使用 devicemapper 驱动利用 LVM 的一些
机制来模拟分层存储。这样的做法除了性能比较差外，稳定性一般也不好，而且配置相对复
杂。Docker 安装在 CentOS/RHEL 上后，会默认选择 devicemapper ，但是为了简化配置，
其 devicemapper 是跑在一个稀疏文件模拟的块设备上，也被称为 loop-lvm 。这样的选择是
因为不需要额外配置就可以运行 Docker，这是自动配置唯一能做到的事情。但是 loop-lvm
的做法非常不好，其稳定性、性能更差，无论是日志还是 docker info 中都会看到警告信
息。官方文档有明确的文章讲解了如何配置块设备给 devicemapper 驱动做存储层的做法，这
类做法也被称为配置 direct-lvm 。
除了前面说到的问题外， devicemapper + loop-lvm 还有一个缺陷，因为它是稀疏文件，所
以它会不断增长。用户在使用过程中会注意到
/var/lib/docker/devicemapper/devicemapper/data 不断增长，而且无法控制。很多人会希望删
除镜像或者可以解决这个问题，结果发现效果并不明显。原因就是这个稀疏文件的空间释放
后基本不进行垃圾回收的问题。因此往往会出现即使删除了文件内容，空间却无法回收，随
着使用这个稀疏文件一直在不断增长。
所以对于 CentOS/RHEL 的用户来说，在没有办法使用 UnionFS 的情况下，一定要配置
direct-lvm 给 devicemapper ，无论是为了性能、稳定性还是空间利用率。
或许有人注意到了 CentOS 7 中存在被 backports 回来的 overlay 驱动，不过 CentOS 里的
这个驱动达不到生产环境使用的稳定程度，所以不推荐使用。

# 备忘

```
export DOCKERURL=https://storebits.docker.com/ee/rhel/sub-43e7d7c4-5ba9-4324-a210-246443ac8d5c
```

`yum-config-manager --add-repo https://storebits.docker.com/ee/rhel/sub-43e7d7c4-5ba9-4324-a210-246443ac8d5c/rhel/docker-ee.repo`
