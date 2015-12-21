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

此实用程序中最常见的一种情况是实时监控实时服务器。默认参数支持此共同模式。

 > ```$ asloglatency -h writes_master```
 
 它返回writes_master下面的直方图： 
 
 
```javascript
  writes_master
  Mar 25 2013 21:58:58
  % > (ms)
  slice-to (sec)      1      8     64  ops/sec
  -------------- ------ ------ ------ --------
  21:59:08    10   1.56   0.09   0.00   1932.3
  21:59:18    10   1.74   0.04   0.00   1937.7
  21:59:28    10   1.25   0.11   0.00   1952.6
  21:59:38    10   1.37   0.08   0.00   1940.3
  21:59:48    10   1.63   0.08   0.00   1946.7
  21:59:58    10   1.34   0.07   0.00   1938.4
  22:00:08    10   1.29   0.08   0.00   1957.7
  22:00:18    10   1.40   0.07   0.00   1947.1
  22:00:28    10   1.28   0.10   0.00   1940.3
  -------------- ------ ------ ------ --------
  avg         1.43   0.08   0.00   1943.0
  max         1.74   0.11   0.00   1957.7
```
 