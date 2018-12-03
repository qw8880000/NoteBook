
# 参考资料

* [Docker 入门教程 - 阮一峰](http://www.ruanyifeng.com/blog/2018/02/docker-tutorial.html)
* [Docker - 中文文档](https://docs.docker-cn.com/)

# docker 在 RHEL 下如何安装

参考教程：[Get Docker EE for Red Hat Enterprise Linux](https://docs.docker.com/install/linux/docker-ee/rhel/#install-from-the-repository)

安装中有个问题，就是提示`container-selinux >= 2.9`，具体解决是：
* `yum-config-manager --enable rhel-7-server-extras-rpms`
* YUM中加入 epel 源

# 备忘

```
export DOCKERURL=https://storebits.docker.com/ee/rhel/sub-43e7d7c4-5ba9-4324-a210-246443ac8d5c
```

`yum-config-manager --add-repo https://storebits.docker.com/ee/rhel/sub-43e7d7c4-5ba9-4324-a210-246443ac8d5c/rhel/docker-ee.repo`
