# 备份和恢复

aerospike提供的能力来备份和恢复您的集群数据。正常情况下，即使出现硬件故障或网络中断，数据复制（在一个集群）和跨数据中心复制（XDR）功能保证数据不会丢失。然而，良好的做法，定期创建备份，从灾难性的数据中心故障或行政事故更容易恢复。

可用备份/恢复实用程序

* asbackup - 备份全部的数据从一个namespace 或者在一个namespace指定 set中，使用标准的aerospike client scan API.
* asrestore - 从一个以前创建的备份恢复namespace 或者 set 数据 ，使用 Aerospike's standard client API

备份/恢复工具是安装包的一部分


## 什么数据备份
备份的选项

* Records记录
  1. 记录元数据（摘要，TTL，生成数，key）
  2. 规则的bin（字符串，整数，二进制）
  3. 复杂的数据类型（CDT）bin（list、map）
  4. 大数据类型（LDT）bin（大列表）
* 二级索引定义
* 用户自定义函数（UDF）模块


## 如何创建备份文件
备份文件是可读的文本文件。详情，见源代码库中的文件格式规范。


运行作为备份的最基本形式是指定群集备份（host），namespace的备份（--namespace），以及备份文件的本地目录（目录）。假设我们有一个集群包含一个IP地址1.2.3.4节点。备份这集群测试namespace目录 backup_2015_08_24，我们会使用下面的命令。


The most basic form of running asbackup is to just specify the cluster to backup (--host), the namespace to backup (--namespace), as well as the local directory for the backup files (--directory). Suppose that we have a cluster that contains a node with IP address 1.2.3.4. To backup the test namespace on this cluster to the directory backup_2015_08_24, we would issue the following command.











