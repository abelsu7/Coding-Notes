> ![](https://notes.abelsu7.top/_media/linux.svg ':no-zoom')Linux 资源收集 <br>
> **Last Update**: `2018-11-14` <br>
> **更新中…**

## 社区推荐

- [Linux 中国]()
- [Tecmint]()
- [mixCraft]()

## 软件推荐

- tmux
- ~~screen~~
- glances
- htop
- tree
- rinetd
- aria2
- fish
- Tuptime

## Bash 命令

- dig
- scp
- pwd
- iftops

## Linux 官网

* [Linux.org](https://www.linux.org/)
* [The Linux Kernel Archieves](https://www.kernel.org/)
* [The Linux Foundation](https://www.linuxfoundation.org/)
* [Linux Documentation](https://linux.die.net/)
* [Linux Man Page](https://linux.die.net/man/)
* [Linux 命令大全](http://man.linuxde.net)
* [Linux KVM](https://www.linux-kvm.org/page/Main_Page)
* [QEMU](https://www.qemu.org/)

## Linux 发行版

### 官网地址

* [![](logo/redhat.svg)RHEL](https://www.redhat.com/en/technologies/linux-platforms/enterprise-linux)
* [![](logo/centos.svg)CentOS](https://www.centos.org/)
* [![](logo/fedora.svg)Fedora](https://getfedora.org/zh_CN/)
* [![](logo/ubuntu.svg)Ubuntu](https://www.ubuntu.com/)
* [![](logo/debian.svg)Debian](https://www.debian.org/)
* [![](logo/opensuse.svg)openSUSE](https://www.opensuse.org/)
* [![](logo/coreos.svg)CoreOS](https://coreos.com/)
* [![](logo/freebsd.ico ':size=16')FreeBSD](https://www.freebsd.org)
* [![](logo/archlinux.svg)Arch Linux](https://www.archlinux.org/)
* [![](logo/alpine.ico ':size=16')Alpine Linux](https://alpinelinux.org/)
* [![](logo/busybox.png ':size=16')BusyBox](https://busybox.net/)
* [![](logo/gentoo.png ':size=16')Gentoo Linux](https://www.gentoo.org/)

### 文章资讯

- [![](logo/wechat.svg)五款主流 Linux 发行版性能对比，稳而不强？| 芋道源码](https://mp.weixin.qq.com/s/oWR0L_-AwE5RshYNFvOC2w)

## 用户管理

- [![](logo/csdn.ico ':size=16')Linux 创建用户、设置密码、修改用户、删除用户 | CSDN](https://blog.csdn.net/sunxx1986/article/details/6854307)

## 底层原理

- [![](logo/wechat.svg)底层原理 - 码农有道![](logo/star.svg)](https://mp.weixin.qq.com/s/OzpgmcCjabT7bKPf1txK4g)
- [![](logo/ruanyifeng.ico ':size=16')计算机是如何启动的？| 阮一峰![](logo/star.svg)](http://www.ruanyifeng.com/blog/2013/02/booting.html)
- [![](logo/ruanyifeng.ico ':size=16')Linux 的启动流程 | 阮一峰![](logo/star.svg)](http://www.ruanyifeng.com/blog/2013/08/linux_boot_process.html)

## CentOS 运维

- [![](logo/wechat.svg)《运维三十六计》：运维生存必备宝典](https://mp.weixin.qq.com/s/VRRNCeSOuebBQ5nPZLwGoA)

### VNC

### SSH

### 修改 yum 源

### 从指定的 yum 源安装软件

```bash
yum install nginx --enablerepo=epel
```

### 升级内核

载入公钥：

```bash
rpm --import https://www.elrepo.org/RPM-GPG-KEY-elrepo.org
```

升级安装 [ELRepo](https://elrepo.org/tiki/tiki-index.php)（注意更新 URL 中的版本号）：

```bash
rpm -Uvh http://www.elrepo.org/elrepo-release-7.0-4.el7.elrepo.noarch.rpm
```

载入`elrepo-kernel`元数据：

```bash
> yum --disablerepo=\* --enablerepo=elrepo-kernel repolist
repo id              repo name                                                             status
elrepo-kernel        ELRepo.org Community Enterprise Linux Kernel Repository - el7         37
repolist: 37
```

查看可用的 RPM 包：

```bash
> yum --disablerepo=\* --enablerepo=elrepo-kernel list kernel*
```

查看当前内核启动顺序：

```bash
> awk -F\' '$1=="menuentry " {print i++ " : " $2}' /etc/grub2-efi.cfg
0 : CentOS Linux (3.10.0-1062.1.2.el7.x86_64) 7 (Core)
1 : CentOS Linux (3.10.0-693.21.1.el7.x86_64) 7 (Core)
2 : CentOS Linux (3.10.0-693.17.1.el7.x86_64) 7 (Core)
3 : CentOS Linux (3.10.0-693.el7.x86_64) 7 (Core)
4 : CentOS Linux (0-rescue-39763f96d9c8455b8ea2e4189b08260c) 7 (Core)
```

之后可参考下列文章：

- [CentOS 7 升级内核至最新 - AdrianDing | 博客园](https://www.cnblogs.com/ding2016/p/10429640.html)
- [CentOS 7.x 系统及内核升级指南 | 简书](https://www.jianshu.com/p/fdf6bb6c5b9c)
- [CentOS 7/6 内核升级的简单方法：借助 ELRepo，用 yum 命令更新内核](https://www.lijiaocn.com/技巧/2019/02/25/centos-kernel-upgrade.html)
- [ELRepo: HomePage](https://elrepo.org/tiki/tiki-index.php)


### 安装 EPEL 扩展包

> **EPEL** (Extra Packages for Enterprise Linux) 是 **Fedora** 小组维护的一个软件仓库项目，为 RHEL/CentOS 提供它们默认不提供的软件包，兼容 RHEL 和 CentOS 这样的衍生版本。<br>

- [![](logo/51cto.ico ':size=16')CentOS安装EPEL扩展包 | 51CTO](http://blog.51cto.com/tong707/2044668)

```bash
yum install epel-release
```

### 关闭 SELinux

查看 SELinux 状态：

```bash
> sestatus -v
SELinux status:                 enabled

> getenforce
Permissive
```

临时关闭 SELinux（无需重启）：

```bash
> setenforce 0 # 设置 SELinux 为 permissive 模式
```

永久关闭 SELinux 需要修改配置文件`/etc/selinux/config`，之后重启机器：

```bash
# This file controls the state of SELinux on the system.
# SELINUX= can take one of these three values:
#     enforcing - SELinux security policy is enforced.
#     permissive - SELinux prints warnings instead of enforcing.
#     disabled - No SELinux policy is loaded.
SELINUX=disabled
# SELINUXTYPE= can take one of these two values:
#     targeted - Targeted processes are protected,
#     mls - Multi Level Security protection.
SELINUXTYPE=targeted
```

### 关闭 IPv6

- [![](logo/star.svg)CentOS 7 关闭 IPv6 | 陈沙克日志](http://www.chenshake.com/centos-7-close-ip-v6/)

### 中文乱码

- [![](logo/star.svg)Linux 系统中文乱码处理集合 | Fishcried](http://fishcried.com/2014-06-22/Linux中文乱码问题处理/)


### polkitd CPU 占用率高

```bash
systemctl restart polkit
```

- [![](logo/ithelp.png)CentOS 7 記憶體問題 - iT 邦幫忙![](logo/star.svg)](https://ithelp.ithome.com.tw/questions/10185797)
- [![](logo/bugzilla.ico ':size=16')Bug 1235681 - /usr/lib/polkit-1/polkitd consumes 20 to 30 % CPU constantly | Red Hat Bugzilla](https://bugzilla.redhat.com/show_bug.cgi?id=1235681)
- [![](logo/centos.svg)polkitd high cpu usage for at least hours | CentOS](https://www.centos.org/forums/viewtopic.php?t=67547)


## yum 包管理

- [![](logo/fedora.svg)EPEL - Extra Packages for Enterprise Linux | Fedora Project Wiki![](logo/star.svg)](https://fedoraproject.org/wiki/EPEL)

```bash
# 1. 安装 
yum install <package> # 安装指定的安装包

# 2. 更新和升级 
yum update            # 全部更新 
yum update <package>  # 更新指定程序包
yum check-update      # 检查可更新的程序 
yum upgrade <package> # 升级指定程序包

# 3. 查找和显示 
yum info              # 列出所有可以安装或更新的包的信息
yum info <package>    # 显示安装包信息
yum list              # 显示所有已经安装和可以安装的程序包 
yum list <package>    # 显示指定程序包安装情况
yum search <package>  # 搜索匹配特定字符的包的详细信息

# 4. 删除程序 
yum remove | erase <package> # 删除程序包
yum deplist <package>        # 查看程序包依赖情况

# 5. 清除缓存 
yum clean packages        # 清除缓存目录下的软件包 
yum clean headers         # 清除缓存目录下的 headers 
yum clean oldheaders      # 清除缓存目录下旧的 headers 
yum clean, yum clean all  # (= yum clean packages; yum clean oldheaders) 清除缓存目录下的软件包及旧的 headers
```

## Linux 命令及 Shell 编程

### 学习资源

- [Linux 工具快速教程 | Linux Tools Quick Tutorials](https://linuxtools-rst.readthedocs.io/zh_CN/latest/#)
- [Linux命令大全](http://man.linuxde.net)
- [Shell正则表达式 | Linux命令大全](http://man.linuxde.net/docs/shell_regex.html)
- [Linux Shell脚本攻略 | Linux命令大全](http://man.linuxde.net/shell-script)
- [![](logo/xiaotudao.ico ':size=16')Linux 常用操作指南 | 小土刀![](logo/star.svg)](https://wdxtub.com/2017/07/10/linux-operation-guide/)
- [![](logo/github.svg)程序猿成长计划 | Github![](logo/star.svg)](https://github.com/mylxsw/growing-up)

### Shell 编程

- [![](logo/wechat.svg)一份 Shell “圣经” 收好 | 编程珠玑](https://mp.weixin.qq.com/s/Rhglp-Co3U6-j0Dgbqe_3w)
- [![](logo/github.svg)pure-bash-bible | A collection of pure bash alternatives to external processes | Github](https://github.com/dylanaraps/pure-bash-bible)
- [![](logo/wechat.svg)快速入门大厂后端面试必备的 Shell 编程 | JavaGuide![](logo/star.svg)](https://mp.weixin.qq.com/s/oUgUXWkBNp1dbRGzlzdLPg)

### 文章教程

* [![](logo/wechat.svg)命令行：增强版 | Linux 中国![](logo/star.svg)](https://mp.weixin.qq.com/s?__biz=MzI1NDQwNDYyMg==&mid=2247485757&idx=1&sn=85087ef9fdd3735cb75f21ddce22b78a&chksm=e9c4f85cdeb3714a822cf264ed012fd9d9a1f3b21f0716d75d86593d91999eea572b4ca144d8&mpshare=1&scene=24&srcid=1101gnc22wsby1uOQIUq4Fpe#rd)
* [![](logo/wechat.svg)一个命令帮你对文本排序 | 编程珠玑](https://mp.weixin.qq.com/s?__biz=MzI2OTA3NTk3Ng==&mid=2649283987&idx=1&sn=6804ce2841bb66b3085172ed45ec8fa0&chksm=f2f9aef4c58e27e26dfae5711c40037a8976c169f3228601517ebe34c4f482b14002308cc508&scene=21#wechat_redirect)
* [![](logo/wechat.svg)Linux常用命令-解压缩篇 | 编程珠玑![](logo/star.svg)](https://mp.weixin.qq.com/s?__biz=MzI2OTA3NTk3Ng==&mid=2649283987&idx=1&sn=6804ce2841bb66b3085172ed45ec8fa0&chksm=f2f9aef4c58e27e26dfae5711c40037a8976c169f3228601517ebe34c4f482b14002308cc508&scene=21#wechat_redirect)
* [![](logo/wechat.svg)如何理解 Linux shell中“2>&1”？| 编程珠玑](https://mp.weixin.qq.com/s?__biz=MzI2OTA3NTk3Ng==&mid=2649284005&idx=1&sn=dc9e9db84ec363d5a0ed7f84bc6ec866&chksm=f2f9aec2c58e27d42eee09ae646e493530d8d0deda822df2ffa2e5153d210b709a6d69272957&scene=21#wechat_redirect)
* [![](logo/wechat.svg)Linux常用命令--系统状态篇 | 编程珠玑![](logo/star.svg)](https://mp.weixin.qq.com/s?__biz=MzI2OTA3NTk3Ng==&mid=2649283877&idx=1&sn=0ee514b242c1134366f9c4f02ea8d781&chksm=f2f9ae42c58e27547e9025d93820482c0bbe82189ce88e73226bb65a72140351587653f5feee&scene=21#wechat_redirect)
* [![](logo/wechat.svg)Linux中的文件查找技巧 | 编程珠玑![](logo/star.svg)](https://mp.weixin.qq.com/s/T0QjzmycVIc2tZJyyrMIfA)
* [![](logo/tecmint.png ':size=16')20 Linux YUM Commands for Package Management | TecMint](https://www.tecmint.com/20-linux-yum-yellowdog-updater-modified-commands-for-package-mangement/)
* [![](logo/cnblogs.svg)yum和apt-get用法及区别 | 小菜鸟![](logo/star.svg)](https://www.cnblogs.com/garinzhang/p/diff_between_yum_apt-get_in_linux.html)
* [![](logo/wechat.svg)如何用九条命令在一分钟内检查 Linux 服务器性能？| 芋道源码![](logo/star.svg)](https://mp.weixin.qq.com/s/WlOQauIxi3iJ0FUB2EpNGw)
* [![](logo/zhihu.svg)如何用九条命令在一分钟内检查Linux服务器性能？](https://zhuanlan.zhihu.com/p/30779538)
* [![](logo/github.svg)三十分钟学会 AWK | 程序员成长计划![](logo/star.svg)](https://github.com/mylxsw/growing-up/blob/master/doc/%E4%B8%89%E5%8D%81%E5%88%86%E9%92%9F%E5%AD%A6%E4%BC%9AAWK.md)
* [![](logo/github.svg)三十分钟学会SED | 程序员成长计划![](logo/star.svg)](https://github.com/mylxsw/growing-up/blob/master/doc/%E4%B8%89%E5%8D%81%E5%88%86%E9%92%9F%E5%AD%A6%E4%BC%9ASED.md)
* [![](logo/zhihu.svg)优秀的命令行工具整理 （一）| LeanCloud 技术专栏](https://zhuanlan.zhihu.com/p/54946696)
* [![](logo/ibm.svg)linux 技巧：使用 screen 管理你的远程会话 | IBM Developer](https://www.ibm.com/developerworks/cn/linux/l-cn-screen/)

## 开源镜像站

- [![](logo/netease.ico ':size=16')网易开源镜像站![](logo/star.svg)](http://mirrors.163.com)
- [![](logo/ali-opsx.png ':size=16')阿里巴巴开源镜像站 - OPSX![](logo/star.svg)](https://opsx.alibaba.com/mirror?lang=zh-CN)
- [![](logo/qcloud.png)腾讯软件源![](logo/star.svg)](https://mirrors.cloud.tencent.com)
- [![](logo/tuna.png ':size=16')清华大学开源软件镜像站 - TUNA![](logo/star.svg)](https://mirrors.tuna.tsinghua.edu.cn)

## 后端开发

- [![](logo/wechat.svg)说说 “后台开发” 需要注意哪几点 | 程序员小灰![](logo/star.svg)](https://mp.weixin.qq.com/s/2iEJTMuvIoxZLCVJWkt0RQ)

## RPC

- [![](logo/wechat.svg)漫话：如何给女朋友解释什么是 RPC | 漫话编程![](logo/star.svg)](https://mp.weixin.qq.com/s/8oX7BloCulSAEFhzfXbFAg)
- [![](logo/juejin.png ':size=16')一篇文章了解RPC框架原理 | 掘金](https://juejin.im/post/5c04ec12e51d4575d131fda8)

## 分布式

- [![](logo/wechat.svg)漫话：如何给女朋友解释什么是分布式和集群？| 漫话编程![](logo/star.svg)](https://mp.weixin.qq.com/s/Yd4JzTjXTWDfTkV1-Q0q_w)
- [![](logo/wechat.svg)毕玄：阿里十年，从分布式到云时代的架构演进之路 | InfoQ![](logo/star.svg)](https://mp.weixin.qq.com/s/FtFxCwaHYWa-ZzO3x1qZWA)
- [![](logo/wechat.svg)云原生时代，分布式系统设计必备知识图谱（内含22个知识点）| 阿里巴巴云原生![](logo/star.svg)](https://mp.weixin.qq.com/s/CMd4GCoZoTsY_FNB1y9DJw)
- [![](logo/wechat.svg)一文读懂分布式架构知识体系（内含超全核心知识大图）| 阿里巴巴云原生![](logo/star.svg)](https://mp.weixin.qq.com/s/XL5zJNNKCpWLxT8LuJgTUg)

## 负载均衡

* [![](https://notes.abelsu7.top/_media/star.svg)关于负载均衡的一切，简单易懂 | 知乎](https://zhuanlan.zhihu.com/p/50769487)
* [![](logo/wechat.svg)【系统架构】什么是负载均衡 | 码农有道![](logo/star.svg)](https://mp.weixin.qq.com/s?__biz=MzIwNTc4NTEwOQ==&mid=2247484809&idx=1&sn=ca740c0b9195ca7aa1e81c4c5f1e5c30&chksm=972ad4f3a05d5de5f524d4883c66144c98a8f4ec450421857592a76fb924c348b704efdbd542&mpshare=1&scene=1&srcid=1101YD6LkiVm4T0AHKPQoTZn#rd)
* [![](logo/wechat.svg)漫话：如何给女朋友解释什么是负载均衡 | 漫话编程![](logo/star.svg)](https://mp.weixin.qq.com/s/fpPoLFx8UYsPO5ExC6oC6A)

## 监控分析

- [使用 promethues 和 grafana 监控自己的 linux 机器 | cizixs![](logo/star.svg)](http://cizixs.com/2018/01/24/use-prometheus-and-grafana-to-monitor-linux-machine/)
* [11 Methods To Find System/Server Uptime In Linux | 2DayGeek![](logo/star.svg)](https://www.2daygeek.com/11-methods-to-find-check-system-server-uptime-in-linux/)
* [Tuptime – A Tool To Report The Historical And Statistical Running Time Of Linux System](https://www.2daygeek.com/tuptime-a-tool-to-report-the-historical-and-statistical-running-time-of-linux-system/)
* [![](logo/star.svg)Glances | 跨平台监控工具](https://nicolargo.github.io/glances/)
* [UptimeRobot](https://uptimerobot.com)
* [Grafana](http://docs.grafana.org)
* [![](https://notes.abelsu7.top/_media/star.svg)5分钟搭建网站实时分析：Grafana+日志服务实战 | 阿里云栖社区](https://yq.aliyun.com/articles/227006#20)
* [可视化工具 Grafana | 简书](https://www.jianshu.com/p/02c4b5c1e804)
* [调试利器：SSH隧道 | 腾讯云+社区](https://cloud.tencent.com/developer/article/1006320)
* [![](logo/wechat.svg)服务器性能指标（一）——负载（Load）分析及问题排查 | Hollis![](logo/star.svg)](https://mp.weixin.qq.com/s?__biz=MzI3NzE0NjcwMg==&mid=2650121338&idx=1&sn=5004157641f29af5384f5f0a7eaf9e98&chksm=f36bb95bc41c304dd6654b5b8ed05adb0726cc8f4875f3cf61bcbca2b290cb3eeb717a95a3c3&scene=21#wechat_redirect)
* [![](logo/wechat.svg)服务器性能指标（二）——CPU利用率分析及问题排查 | Hollis![](logo/star.svg)](https://mp.weixin.qq.com/s?__biz=MzI3NzE0NjcwMg==&mid=2650121526&idx=1&sn=2f492b80d7cdf6a7b47e8f51dfad249f&chksm=f36bb817c41c31017c5e336e78449aa14d4548ee4b64abc2e13ab2c097d13dee170fef2ff731&mpshare=1&scene=1&srcid=1101wOvI8IsuX4Y62ByXJBPq#rd)
* [![](logo/wechat.svg)开源实时监控系统CAT 3.0发布：多语言客户端及多项性能提升 | 美团技术团队](https://mp.weixin.qq.com/s?__biz=MjM5NjQ5MTI5OA==&mid=2651749250&idx=2&sn=704a3c8b92e8221f0a0dfdbd947d9f85&chksm=bd12a2cf8a652bd9d1e1286c6dfb3ca85d46c1e83e958dc594bc21f74ea1a3181866a7e6edab&mpshare=1&scene=24&srcid=1102zqQyTEJQ3xYEwDziTCX4#rd)
* [![](logo/wechat.svg)【开源工具】推荐一款Linux下内存检测工具：valgrind | 码农有道![](logo/star.svg)](https://mp.weixin.qq.com/s/aQoiF43m3oRCK4JksgcCTQ)
* [![](logo/wechat.svg)如何用九条命令在一分钟内检查 Linux 服务器性能？| 芋道源码![](logo/star.svg)](https://mp.weixin.qq.com/s/WlOQauIxi3iJ0FUB2EpNGw)
* [![](logo/zhihu.svg)如何用九条命令在一分钟内检查Linux服务器性能？](https://zhuanlan.zhihu.com/p/30779538)

## Gnome 主题

* [Vimix-Gtk-Theme 主题更新](https://imcn.me/html/y2018/34575.html)

## 面试相关

- [![](logo/wechat.svg)面试 - 互联网公司运维工程师面试点梳理 | LeetCode 力扣![](logo/star.svg)](https://mp.weixin.qq.com/s/cgLe65_IjUm7ZajGDZYKzg)

## 业界资讯

- [![](logo/wechat.svg)2019年可能会是Linux年？| InfoQ](https://mp.weixin.qq.com/s/MRIvydzjbqELG1bswIa0zQ)

## 命令行查单词

?> [![](logo/star.svg)V2EN - Way to English](http://v2en.co/)

```bash
# 在 .bashrc 或 .zshrc 中添加
alias dic='dic(){curl v2en.co/$1;};dic'
```