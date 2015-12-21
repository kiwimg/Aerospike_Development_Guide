# 概要


### 规划[Plan]


本节涵盖了如何规划和选择最佳的硬件配置为您的应用程序。

* Linux 容量规划-计算总存储，内存和吞吐量的硬件要求
* Google Cloud Compute Capacity Planning - performance numbers factored with your application's
* 内存需求将有助于确定合适的机型。
* 服务器硬件 - 确定要使用什么样的硬件
* 闪存存储 - 专门考虑采取闪存存储的优势
* 网络 - aerospike如何使用网络


### 安装
本节介绍如何在Amazon EC2上，不同的Linux发行版，OS X操作系统，Windows和一些云服务提供商安装aerospike。

Install on Linux - how to install on Red Hat, Ubuntu, Debian and other Linux distributions



### 配置
aerospike是一个单个配置文件，在每个数据库节点指定网络参数，命名空间、日志和数据复制。对于一个给定的命名空间，在配置文件中的大多数信息将是相同的。

* Amazon EC2 - recommendations for configuring port, ip address, heartbeat mode, rack awareness and other parameters
* Google Cloud Compute - recommendations for configuring network, firewall, and clusters
* Network - configure port, ip address, heartbeat mode, rack awareness and other parameters
* Namespace - configure data storage location, data retention and data replication
* Log - configure log location and logging level, and learn use of logrotate tool
* Datacenter Replication - establish and configure Cross Datacenter Replication (XDR) for
* Aerospike Enterprise Edition customers (set parameters, establish topology, configure network and specify data replication)
* Non-Root - set-up Aerospike to run as a non-root user

### 升级

### 管理


### 监控 Monitor

### 调优 Tune

### 故障排除 Troubleshoot



###参考手册