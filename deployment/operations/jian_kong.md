# 监控

监控是一个系统关键组成部分。显而易见的理由监控是减少操作响应时间停机事件,如硬件故障和软件错误。大多数监视工具(如Graphite或Nagios)可以提供趋势数据允许你的业务团队有效地识别和解决未来规模障碍。

### 监测解决方案
aerospike有几种不同的方法来监控数据库包括独立的工具和集成第三方插件的插件。


| Tool | Documentation | Alerting 报警 |Trending|
| -- | -- | -- | -- |
| Aerospike Monitoring Console | Aerospike Monitoring Console | Yes | No |
| ASMonitor | ASMonitor | No | No |
| AQL | AQL | No | No |
| Aerospike Logs | Aerospike Logs | Aerospike Logs | yes |
| Graphite| Guide | No* | yes |
| Nagios | Guide | yes | No* |

* Solution has 3rd party plugin for Alerting or Trending