# ascli – Query Management

## query-list

这个命令可以显示在集群上运行的任何查询的列表。如果你指定一个节点/端口,那么只列出了指定节点上运行的查询。该命令的语法是:

>```ascli query-list [-v]```

>```-v: 将打印更详细的清单```

Example:

```
$ ascli query-list
TRANSACTION ID          STATUS
472341955492950239      RUNNING

```

如果加上 -v参数
```
$ ascli query-list -v
NODE               TRANSACTION ID          STATUS     PROGRESS      EXEC TIME(ms)
BB92A20F7290C00    13912474952720922700    RUNNING    [n=191079]    24672587
```

