# 备份 (asbackup)

asbackup作用从aerospike集群备份namespaces或set到本地存储。asbackup同时查询多个集群中的节点。默认情况下,多达10个节点同时备份。这个限制可以改变--parallel令行选项。每个集群节点的数据,备份partition-by-partition（按分区）基础上。如果一个记录创建或更新后分区备份,备份不会反映这一点。

