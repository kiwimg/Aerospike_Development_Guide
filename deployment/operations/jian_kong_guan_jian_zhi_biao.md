# 监控关键指标

下面提供了一组推荐的指标来监测。指标分为6类，每一类表示一个共同的系统组件，可能导致该指标报告一个警告/临界值。该类别如下：

* Application: Application metrics are KPIs that frequently indicate in the customer's application.
* Memory: Memory metrics are KPIs that may be used to indicate abnormal memory utilization.
* Network: Network metrics are KPIs that may indicate problems on the network layer.
* Storage: Storage metrics are KPIs that may be used to indicate abnormal disk utilization.
* Service: Service/Other metrics are KPIs are a mix between metrics that indicate abnormal Database operation (such as migrations outside of a maintenance event) or system problems that may cause abnormal Database operations (such as time skew).服务/其他指标kpi指标表明之间的混合数据库操作异常(如迁移以外的维修事件)或系统问题,可能会导致异常的数据库操作(如时间偏移)。
* Trend: Trend metrics are useful stats to allow operations deeper understanding of system behaviors leading up to a particular event.趋势指标是有用的数据,允许业务深入了解系统行为导致一个特定的事件。


除了监控统计以下操作也应该监控Linux重要点，如空闲磁盘空间、空闲RAM,交换等


##指标表 Metric Table
更多指标查看参考手册章节中的度量指标

| 名称 | 用法 |
| -- | -- |
| available_pct <br>Category: storage<br>Location: namespace  | ```IF available_pct drops below 20% THEN may indicate that defrag is unable to keep up with the current load, warn operations ```<br>```IF available_pct drops below 15% THEN critical alert to operations, usable disk resources are critically low may result in a stop-writes if situation if available_pct drops drops below 5%.``` |
| cluster_size<br>Category: network<br>Location: statistics |``` IF cluster_size does not equal the expected cluster size and cluster in not undergoing maintenance THEN Operations need to investigate the cause.``` |
| hwm-breached<br>Category: storage<br>Location: namespace | ```IF hwm-breached is true THEN alert operations that memory or disk resources are strained, may indicate need to increase cluster capacity. ```|
| stop-writes<br>Category: storage<br>Location: namespace |``` IF stop-writes is true THEN critical alert to operations, system has entered stop-writes mode, until cause is reverted system will reject all writes from the Application.```|
| timediff_lastship_cur_secs<br>Category: service<br>Location: xdr|```Number of seconds it took since the last shipment was logged to when it was finally sent to remote cluster. This is an approximation of latency between what has been comitted locally to what has been shipped.``` |
| xdr-uptime<br>Category: service<br>Location: xdr| ```IF xdr-uptime is below 300 and the cluster is not undergoing maintenance THEN This XDR on this node was restarted within the last 5 minutes.```|


