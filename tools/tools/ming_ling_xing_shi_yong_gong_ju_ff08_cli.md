# 命令行实用工具（CLI）

ascli提供一组命令（get, put, remove, etc）。

## 用法 Usage

>```ascli OPTIONS COMMAND```

## Options
The following are options for ascli:

--path=<path>

Specify the search path for ascli commands (C executables)

--list

List available commands

--help

Show help message

## Commands
The following are commands for ascli. Each command has its own set of options and arguments. See the command's documentation for details.

| Command | Description |
| -- | -- |
| exists | Check if a record exists |
| get| Get a record.|
| put| Put a record.|
| remove | Remove a record. |
| query-list| List the query jobs currently running[列出当前正在运行的查询工作] |
| query-kill | Kill a query job|
| scan-list | List the scan jobs currently running[当前正在运行的扫描的作业列表] |
| scan-kill| Kill a scan job. |
| udf-get| Download a UDF module.[下载一个自定义函数模块] |
| udf-put| Upload a UDF module.[上传一个自定义函数模块]|
| udf-list| List UDF modules.|
| udf-remove| Remove a UDF module |
| udf-record-apply| Apply a UDF to a record.[给记录运行自定义]|


