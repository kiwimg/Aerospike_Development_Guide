# 日志延迟工具（asloglatency）

aerospike日志延迟工具（asloglatency）分析aerospike日志文件和返回延迟测量。它返回一个给定的时间段在表格，易于阅读的形式的延迟分析。本实用程序分析了一种直方图，通过分析在连续时间片中的延迟日志线，并计算每个时间片中的操作的百分比，超过了各种延迟阈值。


## 用法

您在命令行运行该工具，并提供选项参数。使用“帮助”选项来显示选项列表。


> ```asloglatency OPTIONS```


## 选项
| Option | Default | Description |
| -- | -- | -- |
| -l | /var/log/aerospike.log |aerospike 日志文件 |
| -h |  | (required) Name of the histogram to query. |
| -t | 10 | Analysis slice interval in seconds or time format,Time Format: 1:00:00 |
| -f | tail | Log time from which to analyze. May use the following formats: head, 'Sep 22 2011 22:40:14', -3600, or -1:00:00. |
| -d | | Maximum time period to analyze. May use the following formats: 3600 or 1:00:00.|
| -n | 3 | Number of buckets to display.|
| -e | 3| Show the 0-th and then every n-th bucket.|
| -r | Disabled | Run until user presses return key or ctrl-c. ``` Auto enabled if -f tail.``` |



## 例子

