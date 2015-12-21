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
 
 >```按回车键或Ctrl + C停止脚本并显示平均值和最大值。```
 
 直方图桶说明事件的分布。1列包含writes_master未完成在1 ms内第二列包含writes_master未完成后8毫秒计数的计数
 
 
 asloglatency不在0和1之间的增量计算。如果你需要测量亚毫秒延迟时间，你可以测量它们，并计算在客户端的平均值。
 
 
 另一种常见的使用情况是在过去的时间内检查。下面的示例分析读取
 
 >  ```asloglatency -h reads -f -12:00:00 -d 2:00```
 
 分析在日志文件结束前12小时开始。它回顾了2分钟的记录，并在10秒的增量分析数据。
 
 ```javascript
  reads
  Mar 25 2013 22:01:38
  % > (ms)
  slice-to (sec)      1      8     64  ops/sec
  -------------- ------ ------ ------ --------
  22:01:48    10   1.13   0.04   0.00   4661.8
  22:01:58    10   1.00   0.05   0.00   4402.1
  22:02:08    10   0.93   0.03   0.00   4246.7
  22:02:18    10   0.75   0.03   0.00   4161.3
  22:02:28    10   0.87   0.03   0.00   4157.0
  22:02:38    10   0.77   0.04   0.00   4161.2
  22:04:08    10   0.80   0.03   0.00   4213.1
  22:04:19    11   0.94   0.04   0.00   3719.6
  22:04:29    10   1.21   0.03   0.00   4264.7
  22:04:39    10   1.06   0.05   0.00   4101.3
  22:04:49    10   0.78   0.04   0.00   3872.4
  -------------- ------ ------ ------ --------
  avg         0.97   0.04   0.00   4188.0
  max         1.34   0.05   0.00   4661.8
  ```