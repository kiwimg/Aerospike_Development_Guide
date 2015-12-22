# 监控

监控是一个系统关键组成部分。显而易见的理由监控是减少操作响应时间停机事件,如硬件故障和软件错误。大多数监视工具(如Graphite或Nagios)可以提供趋势数据允许你的业务团队有效地识别和解决未来规模障碍。

### 监测解决方案
aerospike有几种不同的方法来监控数据库包括独立的工具和集成第三方插件的插件。


| Tool | Documentation | Alerting 报警 |Trending|
| -- | -- | -- | -- |
| Aerospike Monitoring Console |[ Aerospike Monitoring Console](http://www.aerospike.com/docs/amc) | Yes | No |
| ASMonitor | [ASMonitor](http://www.aerospike.com/docs/tools/asmonitor/) | No | No |
| AQL | AQL | No | No |
| Aerospike Logs | [Aerospike Logs](http://www.aerospike.com/docs/operations/monitor/latency/) | Aerospike Logs | yes |
| Graphite| [Guide ](http://www.aerospike.com/docs/operations/monitor/graphite/)| No* | yes |
| Nagios | [Guide](http://www.aerospike.com/docs/operations/monitor/nagios/) | yes | No* |

* Solution has 3rd party plugin for Alerting or Trending