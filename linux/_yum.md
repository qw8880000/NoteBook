# 工作原理
  - [深入理解yum工作原理](http://www.firefoxbug.com/index.php/archives/2777/)
  - [yum介绍、工作原理](https://blog.csdn.net/WYpersist/article/details/79932991)
  - [yum](http://yum.baseurl.org/index.html)

# 常用操作
  - `yum repolist`: 查看使用了哪些YUM源
  - `yum clean all`
  - `yum makecache`

# 常见路径
  - 配置文件：`/etc/yum.conf`
  - yum源：`/etc/yum.repos.d`

# 源
  - 阿里云的yum源: `http://mirrors.aliyun.com/repo/`
  - 网易yum源：登陆`http://mirrors.163.com/`，查找适合自己系统的源，然后点击`xx使用帮助`

# epel

EPEL的全称叫 Extra Packages for Enterprise Linux 。EPEL是由 Fedora 社区打造，为 RHEL 及衍生发行版如 CentOS、Scientific Linux 等提供高质量软件包的项目。装上了 EPEL之后，就相当于添加了一个第三方源。

# 遇到的问题

**yum 提示 bad id for repo**

原因：`/etc/yum.repos.d`中，有一个repo配置有问题，语法有误

**yum 提示 http://mirrors.cloud.aliyuncs.com/centos/7Server/os/x86_64/repodata/repomd.xml: [Errno 14] curl#6 - "Could not resolve host: mirrors.cloud.aliyuncs.com; Name or service not known"**

原因：repo中的`baseurl=http://mirrors.aliyun.com/centos/$releasever/os/$basearch/` 有一个 `$releasever`变量，这个变量的值是`7Server`，但是服务器的真实路径应该是`7`。

解决：
  - `sh -c 'echo "7" > /etc/yum/vars/centosver'`
  - 把repo中的 `$releasever` 全部替换成 `$centosver`
