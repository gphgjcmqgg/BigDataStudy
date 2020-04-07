# hadoop

1. hadoop是一个由Apache基金会所开发的分布式系统基础架构
2. 主要解决，海量数据的存储和海量数据的分析计算问题

## hadoop的优势

1. 高可靠性
2. 高扩展性
3. 高效性
4. 高容错性

## hadoop1.x和hadoop2.x区别

在hadoop1.x时代，hadoop中的MapReduce同时处理业务逻辑运算和资源调度，耦合性较大，在hadoop2.x时代，增加了Yarn。Yarn只负责资源的调度，MapReduce只负责运算。
hadoop1.x组成： MapReduce（计算+资源调度）HDFS（数据存储）、Common（辅助工具）
hadoop2.x组成： MapReduce（计算）、Yarn（资源调度）、HDFS（数据存储）、Common（辅助工具）

# HDFS架构概述

1. NameNode（nn）
2. DataNode(dn)
3. Secondary NameNode(2nn)

## YARN架构概述

1. ResouceManager(RM)
    1)处理客户端请求    2）监控NodeManager  3）启动或监控ApplicationMaster  4）资源的分配与调度
2. NodeManager(NM)
    1）管理单个节点上的资源 2）处理来自ResouceManager的命令 3）处理来自ApplicationMaster的命令
3. ApplicationMaster(AM)
    1）负责数据的切分   2）为应用程序申请资源并分配给内部的任务 3）任务的监控与容错
4. Container
    Container是YARN中的资源抽象，它封装了某个节点上的多维度资源，如内存、CPU、键盘、网络等。

## MapReduce架构概述

MapReduce将计算过程分为两个阶段：Map和Reduce
1）Map阶段并行处理输入数据
2）Reduce阶段对Map结果进行汇总

## Hadoop运行环境搭建

1. 克隆虚拟机
2. 修改克隆虚拟机的静态IP
3. 修改主机名
4. 关闭防火墙
5. 创建hadoop用户
6. 配置hadoop用户具有root权限
7. 在/opt目录下创建文件夹
    （1） 在/opt目录下创建module、software文件夹
    [hadoop@hadoop100 opt]$ sudo mkdir module
    [hadoop@hadoop100 opt]$ sudo mkdir software
    （2）修改module、software文件夹的所有者cd
    [hadoop@hadoop100 opt]$ sudo chown atguigu:atguigu module/ software/

vim /etc/udev/rules.d/70-persistent-net.rules
配置网络
vim /etc/sysconfig/network-scripts/ifcfg-eth0
修改主机名称
vim /etc/sysconfig/network
ip地址与主机映射
vim /etc/hosts
vim /etc/sudoers