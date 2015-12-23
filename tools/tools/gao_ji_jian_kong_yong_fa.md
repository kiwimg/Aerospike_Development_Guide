# 高级监控用法 asmonitor - Creating New Tables

asmonitor允许您创建持久性表，用来监视某些统计数据，在这个表中您可以监视统计数据列表

asmonitor allows you to create persistent tables for monitoring certain statistics. The list of statistics that you can monitor is in the reference.


一旦你创建了表定义，你可以显示表和表的名称将显示在可用表的列表中。
Once you create your table definition, you can display the table and the table name will be shown in the list of available tables.

例如,如果您想监视悬而未决的数量限制错误,你asmonitorsession创建表定义和显示，类似下面这样:

For example, if you wanted to monitor the number of pending limit errors, your asmonitorsession to create the table definition and display the table would look like this:

```
Monitor> createtable
Create new table (response n if you do not want to create) (Y/n)? y
Enter Table name : PendingLimit
table name= PendingLimit
Type of table (node,namespace,xdr,sets) : node
Table type= node
---------------
List of keys allowed for reference: tscan_pending , err_rw_request_not_found , partition_ref_count , rw_err_dup_internal , ....[List of all available stat names] , stat_proxy_errs ,
---------------
Enter the Number of Columns in the table(excluding 1st column as it will be IP:port) : 1
1st column will be Node IP
Enter Name of 1 Column in the table: Pending Limit Errors
Enter key for Pending Limit Errors Column in the table: err_rw_pending_limit
Table PendingLimit created!
Monitor> info
Namespace     Node          PendingLimit  SETS          XDR          
Monitor> info PendingLimit

 === PENDINGLIMIT ===
Node IP                 Pending
                          Limit
                         Errors
u10.aerospike.local         86
u11.aerospike.local          0
u9.aerospike.local          12
No. of rows: 3
Monitor>
```


##Displaying Tables