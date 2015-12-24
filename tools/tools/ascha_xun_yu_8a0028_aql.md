# as查询语言(AQL)

### List Namespaces

下面的命令列出namespaces 列表
>```SHOW NAMESPACES```

Example:
```
aql> show namespaces
+------------+
| namespaces |
+------------+
| "test"     |
| "bar"      |
+------------+
2 rows in set (0.001 secs)
```

### List Sets

The following command lists all sets:

>```SHOW SETS```

Example:
```
aql> show sets
+---------+-----------+-----------+------------+-----------+---------+
| ns_name | set_name  | n_objects | stop-write | evict-hwm | delete  |
+---------+-----------+-----------+------------+-----------+---------+
| "test"  | "newtest" | 11        | 0          | 0         | "false" |
| "test"  | "users"   | 1         | 0          | 0         | "false" |
+---------+-----------+-----------+------------+-----------+---------+
2 rows in set (0.001 secs)
```


## List Bins
The following command lists all bins:

>```SHOW BINS```
Example:

```
aql> show bins
+-----------+-------+-------+-----------+
| namespace | count | quota | bin       |
+-----------+-------+-------+-----------+
| "test"    | 5     | 32768 | "b"       |
| "test"    | 5     | 32768 | "c"       |
| "test"    | 5     | 32768 | "a"       |
| "test"    | 5     | 32768 | "SUCCESS" |
| "test"    | 5     | 32768 | "name"    |
+-----------+-------+-------+-----------+
5 rows in set (0.000 secs)
```
## List Record Details
Note: explain select is available in Aerospike Tools package 3.6.1 and above.

The following command displays details for a single record:

>```explain select * from <ns>.<set> where PK=<primary key value>```
Example:

```
aql> explain select * from test.uqr where PK=1
[
{
"SET": "uqr",
"DIGEST": "42 7A 64 AE 7B 80 EE 02 3D B8 E9 00 8A F3 FF B0 7F DA EB 58",
"NAMESPACE": "test",
"PARTITION": 2626,
"STATUS": 2,
"UDF": "FALSE",
"TIMEOUT": 1000,
"NODE": "1771FE6C15290C00",
"POLICY": "AS_POLICY_REPLICA_MASTER",
"KEY_POLICY": "AS_POLICY_KEY_SEND"
}
]
```