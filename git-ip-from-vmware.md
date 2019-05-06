之前在做项目的时候主机IP地址、网关、DNS、子网掩码等都是公司或者对方直接给提供的，但是如果我们自己想搭建一台虚拟机或者一台集群的话，手头又没有IP地址，该肿么办呢？

首先，保证你的虚拟机或者服务器安装好了系统，这里以CentOS6.7版本进行说明，具体的操作教程如下。

1、当我们创建好虚拟机之后，直接在命令行中输入命令查看IP地址，得到的往往如下图所示，即便是你怎么调整NAT模式亦或是桥接模式，不会起到太大的作用。

​     commad  ：  ifconfig  -a

2、此时就需要更改虚拟机的网络配置文件，在CentOS6.7中，该网络配置文件在/etc/sysconfig/network-scripts/ifcfg-eth0里边。

3、需要改动的地方只有一个，你没有看错，就只有一个，只需将ONBOOT的值由之前的“no”改为现在的“yes”即可，如下图所示，而且wq保存退出即可。

4、可以通过cat命令查看文件内容是否更改成功

​     command ： cat  /etc/sysconfig/network-scripts/ifcfg-eth0

5.关闭防火墙

​    cmmand：  service iptables  stop

6.重启网络

   cmmand ： service  network  restart

7.再次查看ip？  ifconfig -a

8.ping www.baidu.com   试试

如此一来，我们就可以顺利的获取IP地址，可以继续我们后续的操作，如搭建分布式、CDH集群等操作了。

其实大部分我们用nat模式固定ip的哈哈哈哈哈哈哈 想不到吧