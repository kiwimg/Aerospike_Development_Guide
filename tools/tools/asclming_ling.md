# ascl命令

Ascli 提供一组命令 (get, put, remove, etc) 在Aerospike database上执行


### 用法

ascli的基本用法：

```ascli OPTIONS COMMAND```


### 选项

以下是可供选择的ascli：

* --path=<path>

 对于ascli命令指定的搜索路径（C语言的可执行程序）

* --list

  list可用的命令列表

* --help
 
   Show help message


## 命令Commands

以下是ascli命令。每一个命令都有它自己的一套选项和参数。查看命令的详细文档。

| Command | Description |
| -- | -- |
| exists | 	Check if a record exists.|
| get | Get a record. |
| put | Put a record. |
| 0:5 | 1:5 |
| 0:6 | 1:6 |
| 0:7 | 1:7 |
| 0:8 | 1:8 |
| 0:9 | 1:9 |
| 0:10 | 1:10 |
| 0:11 | 1:11 |
| 0:12 | 1:12 |
| 0:13 | 1:13 |
| 0:14 | 1:14 |

	

	

remove	Remove a record.
query-list	List the query jobs currently running.
query-kill	Kill a query job.
scan-list	List the scan jobs currently running.
scan-kill	Kill a scan job.
udf-get	Download a UDF module.
udf-put	Upload a UDF module.
udf-list	List UDF modules.
udf-remove	Remove a UDF module.
udf-record-apply	Apply a UDF to a record.
