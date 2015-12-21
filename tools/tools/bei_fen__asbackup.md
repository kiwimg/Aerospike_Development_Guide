# 备份 (asbackup)

asbackup作用从aerospike集群备份namespaces或set到本地存储。asbackup同时查询多个集群中的节点。默认情况下,多达10个节点同时备份。这个限制可以改变--parallel令行选项。每个集群节点的数据,备份partition-by-partition（按分区）基础上。如果一个记录创建或更新后分区备份,备份不会反映这一点。

>当集群数据进行迁移(即。再平衡由于节点故障),任何备份可能不是完全一致的。可能会有相同的记录或失踪的多个副本记录。使用——no-cluster-change选项asbackup中止,如果它检测到等待迁移

运行带着--directory 参数选项,asbackup在指定的路径创建多个.asb备份文件。包括所有创建的备份文件。另外,--output-file 使得asbackup存储在单个文件的完整备份。如果是指定的文件,asbackup写入到标准输出（stdout）。这允许管道:

当运行的目录选项，创建多个作为备份。在给定的目录ASB的备份文件。备份由所有创建的文件组成。另外，输出文件作为备份存储在单个文件的完整备份。如果指定的文件，作为备份的备份写入到标准输出,通过允许管道方式输出：

>```asbackup --output-file - [...] | gzip -1 [...] >backup.asb.gz```
