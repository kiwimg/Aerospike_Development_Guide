# as管理工具(asadm)

Aerospike Admin是一个交互式python工具主要用于获取当前集群的健康的摘要信息和跨集群执行动态配置和调优命令。


Aerospike Admin 是Aerospike-Tools包包含在我们提供的服务器安装包里。你可以通过erospike-Admin库获得它


通过asadm ——help 命令可以查看asadm的列表参数。


```javascript

asadm --help
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


执行asadm后您将会收到一个 'Admin>' 提示,提示式帮助和命令的列表和说明，按回车。


```javascript
Admin> help
Aerospike Admin
  - asinfo:
    "asinfo" provides raw access to the info protocol.
      Options:
        -v <command>  - The command to execute
        -p <port>     - The port to use.
                        NOTE: currently restricted to 3000 or 3004
        -l            - Replace semicolons ";" with newlines.
    Modifiers: like, with
    Default: Executes an info command.
  - clinfo:
    "asinfo" provides raw access to the info protocol.
      Options:
        -v <command>  - The command to execute
        -p <port>     - The port to use.
                        NOTE: currently restricted to 3000 or 3004
        -l            - Replace semicolons ";" with newlines.
    Modifiers: like, with
    Default: Executes an info command.
  - cluster:
    Modifiers: with
      - dun:
      - undun:
  - exit:
    Terminate session
  - help:
    Returns documentation related to a command
    for example, to retrieve documentation for the "info"
    command use "help info".
  - info:
    The "info" command provides summary tables for various aspects
    of Aerospike functionality.
    Modifiers: with
    Default: Displays service, network, namespace, and xdr summary
    information.
      - namespace:
        Displays summary information for each namespace.
      - network:
        Displays network information for Aerospike, the main
        purpose of this information is to link node ids to
        fqdn/ip addresses.
      - service:
        Displays summary information for the Aerospike service.
      - xdr:
        Displays summary information for Cross Datacenter
        Replication (XDR).
  - show:
    "show" is used to display Aerospike Statistics and
    configuration.
      - config:
        "show config" is used to display Aerospike configuration settings
        Modifiers: like, with
        Default: Displays service, network, namespace, and xdr configuration
          - namespace:
            Displays namespace configuration
          - network:
            Displays network configuration
          - service:
            Displays service configuration
          - xdr:
            Displays XDR configuration
      - distribution:
        "distribution" is used to show the distribution of object sizes
        and time to live for node and a namespace.
        Modifiers: like, with
        Default: Shows the distributions of Time to Live and Object Size
          - eviction:
            Shows the distribution of Eviction TTLs for namespaces
          - object_size:
            Shows the distribution of Object sizes for namespaces
          - time_to_live:
            Shows the distribution of TTLs for namespaces
      - latency:
        Modifiers: like, with
        Default: Displays latency information for Aerospike cluster.
      - statistics:
        Displays statistics for Aerospike components.
        Modifiers: like, with
        Default: Displays bin, set, service, namespace, and xdr statistics
          - bins:
            Displays bin statistics
          - namespace:
            Displays namespace statistics
          - service:
            Displays service statistics
          - sets:
            Displays set statistics
          - xdr:
            Displays xdr statistics
  - watch:
    "watch" Runs a command for a specified pause and iterations.
    Usage: watch [pause] [iterations] [command]
       pause:      the duration between executions.
                   [default: 2 seconds]
       iterations: Number of iterations to execute command.
                   [default: until keyboard interrupt]
    Example 1: Show "info network" 3 times with 1 second pause
               watch 1 3 info network
    Example 2: Show "info namespace" with 5 second pause until
               interrupted
               watch 5 info namespace
               

```
