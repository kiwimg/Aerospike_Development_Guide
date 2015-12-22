# 延迟[Latency] 从 aerospike 日志获取

默认情况下,每十秒生成一些直方图数据生成到日志文件,主要的有4个

| Type of Histogram Data | Description |
| -- | -- |
| reads | Time taken for read requests from the time they are received at the node to when the response leaves the node |
| writes_master | Time taken for writes from end-to-end (includes the time taken for replica write).|
| proxy | Time for completion of proxy requests from the time they are received at the node to when the response leaves the node. A proxy is a read or write request that arrives at a node, but the node is not the data master for that data, so the request is forwarded to the correct node for processing. The time for completing proxy requests is higher because the node does not handle the request itself, it must wait for the correct node to respond and then forward the response back to the client. |
| writes_reply | Normally this can be ignored and is very similar to the writes_master data. If you have set fire-and-forget mode (this is not common), then this histogram data shows the end-to-end time for write requests, but without waiting for confirmation from the replica that the write has been completed.|


对于每个直方图数据,以下跟踪时间间隔:

| Interval间隔 | 完成所需的时间 |
| -- | -- |
| 0 | 0 to 20 ms ( ≥ 0 ms to < 1 ms ) |
| 1 | 20 to 21 ms ( ≥ 1 ms to < 2 ms ) |
| 2 | 21 to 22 ms ( ≥ 2 ms to < 4 ms ) |
| 3 | 22 to 23 ms ( ≥ 4 ms to < 8 ms )|
|etc| … |


日志文件中，每一组直方图数据看起来像这样

>```[timestamp/tracking] histogram dump: type (number of cumulative transactions for this node)```

>```[timestamp/tracking] (interval: number of transactions) (interval: number of cumulative transactions) etc.```


默认, 每隔10秒生成四组直方图(histogram)数据, 如上所述每一种类型的histogram dump (reads, writes_master, proxy and writes_reply). 这些数字是自上次aerospike服务开始累积. 一组典型的直方图数据（所有读请求）可能看起来像这样：

```java 
Aug 24 2012 18:02:35 GMT: INFO (info): (hist.c:49) histogram dump: reads (90443310 total)
Aug 24 2012 18:02:35 GMT: INFO (info): (hist.c:64) (00: 0089886682) (01: 0000180363) (02: 0000107252) (03: 0000150313)
Aug 24 2012 18:02:35 GMT: INFO (info): (hist.c:64) (04: 0000091264) (05: 0000024060) (06: 0000003137) (07: 0000000154)
Aug 24 2012 18:02:35 GMT: INFO (info): (hist.c:72) (08: 0000000035) (09: 0000000029) (10: 0000000021)
```

在上面的例子中, 该节点从上一次aerospike启动有总共90,443,310读的请求，这种情况下，第9个与最后一个间隔显示读取，完成了在2<sup>9</sup> to 2<sup>10</sup> ms 毫秒（512毫秒到1024毫秒）。第二行显示89886682的交易都在0区间处理（在1毫秒）以来的正常运行时间。所以99.4%的交易处理在1 ms的累积。180363要求在1-2毫秒完成，107252要求在2-4毫秒完成，等等，最后的第十区间，只有21的交易（9000万）完成了512-1024 MS。

第二行显示,89886682个事务处理在0间隔(在1 ms)从正常运行时间。99.4%的交易处理累计在1毫秒。180363请求完成1 - 2女士,女士在2 - 4完成107252个请求,等等。在第十和最后的时间间隔,就21交易(9000万)512 - 1024 ms。



### Histogram Data说明解释

```java 
Feb 21 2013 19:29:29 GMT: INFO (info): (hist.c:49) histogram dump: reads (77160037 total)
Feb 21 2013 19:29:29 GMT: INFO (info): (hist.c:64)  (00: 0062856557)  (01: 0006010842)  (02: 0002984053)  (03: 0001201477) 
Feb 21 2013 19:29:29 GMT: INFO (info): (hist.c:64)  (04: 0000528804)  (05: 0000526571)  (06: 0000479380)  (07: 0000307062) 
Feb 21 2013 19:29:29 GMT: INFO (info): (hist.c:64)  (08: 0000248506)  (09: 0000343465)  (10: 0000536859)  (11: 0000533880) 
Feb 21 2013 19:29:29 GMT: INFO (info): (hist.c:72)  (12: 0000491292)  (13: 0000111289)
```