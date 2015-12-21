# 备份和恢复

aerospike提供的能力来备份和恢复您的集群数据。正常情况下，即使出现硬件故障或网络中断，数据复制（在一个集群）和跨数据中心复制（XDR）功能保证数据不会丢失。然而，良好的做法，定期创建备份，从灾难性的数据中心故障或行政事故更容易恢复。

可用备份/恢复实用程序

* asbackup - 备份全部的数据从一个namespace 或者在一个namespace指定 set中，使用标准的aerospike client scan API.
* asrestore - 从一个以前创建的备份恢复namespace 或者 set 数据 ，使用 Aerospike's standard client API

备份/恢复工具是安装包的一部分


## 备份那些数据
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


运行作为备份的最基本形式是指定群集备份（host），namespace的备份（--namespace），以及备份文件的本地目录（目录）。假设我们有一个集群包含一个IP地址1.2.3.4节点。备份“test” namespace目录 backup_2015_08_24，我们会使用下面的命令。

>```$ asbackup --host 1.2.3.4 --namespace test --directory backup_2015_08_24```

备份程序 asbackup 读取records从集群中进行备份并且存储在指定的目录，在命令行指定--directory参数，备份程序在路径下生成一个set备份文件。默认情况下，每个备份文件限制为250MIB。当了这个极限,asbackup开始一个新文件。另外，集群可以备份到一个文件或标准输出文件而不是使用-目录

——no-cluster-change选项中止备份,如果集群节点发生故障时备份。节点故障导致集群平衡,因此,节点之间数据迁移。流产的备份,数据重新分配完成后请重新启动它。


如果备份失败，备份文件创建了这一点会保持在，默认情况下，asbackup不会覆盖现有的备份文件。重新启动备份时，您可以备份到另一个目录或文件，或使用删除文件已作为备份删除现有的备份文件。


##如何恢复数据

备份是cluster-agnostic。该群集的大小和配置可以完全不同于数据恢复的群集的大小和配置。例如数据从5节点集群备份,可以恢复到4-node或7-node集群。恢复过程总是均匀地将数据分布到集群节点。

asrestore运行的最基本的形式是指定群集恢复（主机）和本地目录包含备份文件（目录）。假设我们有一个集群包含一个IP地址1.2.3.4节点。恢复从目录backup_2015_08_24备份，我们采用下面的命令

>```$ asrestore --host 1.2.3.4 --directory backup_2015_08_24```

默认情况下,备份恢复到命名空间,这是来自。--namespace选项可以用来恢复到一个不同的--namespace。假设以上备份namespace test ,我们想恢复namespace。我们采用下面的命令。

>```$ asrestore --host 1.2.3.4 --directory backup_2015_08_24 --namespace test,prod```

asrestore读取备份文件从指定的路径带着--directory选项。或者,如果备份包含一个--output-file 选项创建的输入文件作为备份，the --input-file 选项 可以使asrestore读取单个文件或标准输入。


## 写的策略 The Write Policy

读取数据恢复到一个namespace在一个集群中使用标准的client API来存储records。namespace可能已经包含现有records,默认情况下,写策略如下机制运行。

* If the record from the backup is expired (based on its TTL value), it is ignored.
* If the record does not exist in the namespace, it is restored from the backup.
* If a newer version of the record (higher or same generation count) exists in the namespace, the record from the backup is ignored.
* If an older version of the record (lower generation count) exists in the namespace, the record is restored from the backup. If the record in the namespace contains bins that are not present in the backup, those bins are preserved.

