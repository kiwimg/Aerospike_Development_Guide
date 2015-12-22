# as管理工具(asadm)

Aerospike Admin是一个交互式python工具主要用于获取当前集群的健康的摘要信息和跨集群执行动态配置和调优命令。


Aerospike Admin 是Aerospike-Tools包包含在我们提供的服务器安装包里。你可以通过erospike-Admin库获得它


通过asadm ——help 命令可以查看asadm的列表参数。


>```asadm --help
usage: asadmin [-h HOST] [-p PORT] [-U USER] [-P [PASSWORD]] [-e EXECUTE] [-u]

optional arguments:
-h HOST, --host HOST  Address (ip/fqdn) of a host in an Aerospike cluster
                      [Default: localhost]
-p PORT, --port PORT  Aerospike service port used by the host.
                      [Default: 3000]
-U USER, --user USER  user name
-P [PASSWORD], --password [PASSWORD]
                      password
-e EXECUTE, --execute EXECUTE
                      Execute a single asadmin command and exit
-u, --help            show program usage

```