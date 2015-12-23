# 用户指南

## Install
asadm默认在发布的安装包里，或者从github仓库获取安装

## Getting Help

1. Run asadm --help to learn about arguments that may be needed for your environment.
2. To start the interactive shell run asadm -h [HOST_IP].
3. From the Admin> prompt run help to see a complete list of supported commands.

## Command Organization(组成 结构）

命令被组织成一个层次结构,类似命令共享一个共同的源(parent)。每个命令可以支持一个或多个修改，可以限制命令到一个特定的组节点或过滤一个命令的输出。

所有的命令会输出基于asadm选择为节点的节点名称。节点名称是最短的独特的前缀完全限定域名(FQDN)或或IP如果域名无法解析。
All commands will sort output based on the node name that asadm chooses for the node. The node name is the shortest unique prefix of Fully Qualified Domain Name (FQDN) or IP if the FQDN cannot be resolved.

## Command Shortcuts[命令快捷键]


所有的命令都支持tab自动补全功能；在Admin>提示符,输入i 按<tab>键将出现完整的info命令，输入cl 按<tab>将会出现建议的列表。您还可以是短命令执行，例如，运行info，你可以输入i和net等同于 info network，将会输出namespace和网络信息

```
Admin> i net
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~Network Information~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
          Node               Node                  Fqdn                    Ip   Client     Current     HB        HB   
             .                 Id                     .                     .    Conns        Time   Self   Foreign   
172.16.245.231   *BB9E2CC3C565000   172.16.245.231:3000   172.16.245.231:3000        2   153238334      0     19919   
172.16.245.232   BB99D5237565000    172.16.245.232:3000   172.16.245.232:3000        2   153238336      0     26505   
172.16.245.233   BB9A63527565000    172.16.245.233:3000   172.16.245.233:3000        2   153238337      0     19909   
172.16.245.234   BB9490B30565000    172.16.245.234:3000   172.16.245.234:3000        2   153238339      0     26493   
Number of rows: 4

Admin> i n
ERR: Ambiguous command: 'n' may be namespace or network.
```
## Modifiers
There are currently two modifiers that commands may support.
目前有两个命令可能支持的修饰符。

* like: Like shows the output containing any word listed after 'like'.
* with: With specifies a list of nodes to be used with the given command.
  You can use the node's IP, FQDN, or Node ID as well as any unique prefix.

## Help

```
Admin> help info
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
```


## Show

```
Admin> show config network like heartbeat mesh
~~~~~~~~~~~~~~~~~~~~~~~~~~Network Configuration~~~~~~~~~~~~~~~~~~~~~~~~~~
NODE              :   u10               u12               u13
heartbeat-address :   192.168.120.110   192.168.120.112   192.168.120.113
heartbeat-interval:   150               150               150
heartbeat-mode    :   mesh              mesh              mesh
heartbeat-port    :   3002              3002              3002
heartbeat-protocol:   v2                v2                v2
heartbeat-timeout :   10                10                10
mesh-address      :   192.168.120.112   192.168.120.112   192.168.120.112
mesh-port         :   3002              3002              3002
```
####Configuration

```
Admin> show config network like heartbeat mesh
~~~~~~~~~~~~~~~~~~~~~~~~~~Network Configuration~~~~~~~~~~~~~~~~~~~~~~~~~~
NODE              :   u10               u12               u13
heartbeat-address :   192.168.120.110   192.168.120.112   192.168.120.113
heartbeat-interval:   150               150               150
heartbeat-mode    :   mesh              mesh              mesh
heartbeat-port    :   3002              3002              3002
heartbeat-protocol:   v2                v2                v2
heartbeat-timeout :   10                10                10
mesh-address      :   192.168.120.112   192.168.120.112   192.168.120.112
mesh-port         :   3002              3002              3002
```


####Distribution（分布式）
The show distribution displays histograms and supports the eviction, object_size, and time_to_live histograms.

```
Admin> show distribution time_to_live 
~~~~~~~~~~~~~~~~~~~~~~~~~phobos_sindex - TTL Distribution in Seconds~~~~~~~~~~~~~~~~~~~~~~~~~~
       Percentage of records having ttl less than or equal to value measured in Seconds
Node      10%      20%      30%      40%      50%      60%      70%      80%      90%     100%
u10    328320   331776   335232   338688   338688   342144   342144   345600   345600   345600
u12    328320   331776   335232   338688   338688   342144   342144   345600   345600   345600
u13    328320   331776   335232   338688   338688   342144   342144   345600   345600   345600
Number of rows: 3
```
###Latency（延迟）
The show latency command displays latency characteristics of reads, writes, and proxies.
```
Admin> show latency like writes_master
~~~~~~~~~~~~~~~~~~~~writes_master Latency~~~~~~~~~~~~~~~~~~~~
Node                     Time   Ops/Sec   >1Ms   >8Ms   >64Ms
   .                     Span         .      .      .       .
u10    23:32:20-GMT->23:32:30    2044.7   1.09    0.0     0.0
u12    23:32:20-GMT->23:32:30    2012.6   0.77    0.0     0.0
u13    23:32:20-GMT->23:32:30    1968.9   1.03    0.0     0.0
Number of rows: 3
```

## Cluster