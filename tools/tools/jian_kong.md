# 监控Aerospike Monitor - asmonitor

在集群中开始监控as性能的时候使用Aerospike的asmonitor命令工具，调整配置设置和诊断问题。这些页描述如何运行asmonitor和各种命令，您可以使用从asmonitor控制台来监控你的Aerospike数据库。

asmonitor安装在‘/opt/aerospike/bin/asmonitor’，asmonitor可以得到服务器和集群的统计信息，并且显示一个容易约读的格式，asmonitor也允许动态改变节点或者集群的配置参数，从asmonitor输出可以定制显示不同的值。


asmonitor工具是一个控制台,您可以输入各种命令(包括大部分的- v的字符串在asinfo命令)。



你可以从任何一台有访问网络运行asmonitor。运行asmonitor使用命令

>```asmonitor [-h <host>[:<port>]] [-p <port>]  [-c <config>]```


-h 表示一个 hostnames or IP 地址 

-h参数是服务器的主机名。该参数是可选的，并且将默认为未指定的端口指定的端口。如果没有指定的端口号，则该选项指定主机被询问的默认端口。该-p是可选的，如果没有指定，那么它将默认为3000。


的参数是服务器的主机名。—p选项如果不指定，采用默认为指定的港口。那么它将默认为3000。


你第一次使用asmonitor必须使用-h选项指定一个种子节点。如果没有指定H，那么它将默认为localhost。一旦连接到节点，那么集群中的其他节点会自动发现。后续的调用asmonitor不要因为配置保存在配置文件需要种子节点。
