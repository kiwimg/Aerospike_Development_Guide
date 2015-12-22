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


