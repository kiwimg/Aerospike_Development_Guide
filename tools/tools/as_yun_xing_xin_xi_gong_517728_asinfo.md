# As 运行信息工具(asinfo)

asinfo是一个命令行实用程序,它提供了一个接口的Aerospike集群指挥和控制功能。这包括的能力改变Aerospike运行时服务器配置参数。

>通过asinfo命令更改配置不会持久化到配置文件中。如果需要持久性改变，则需要手动添加到配置文件中。


## 用法
这个asinfo命名默认会安装在/usr/bin/asinfo，使用语法格式

>```asinfo [-h HOST] [-p PORT] [-v VALUE] [-l]```

| Option | Default | Description|
| -- | -- | -- |
| -h | localhost | IP Address or FQDN of the target Aerospike server. |
| -p | 3000 | 	Service port of the target Aerospike server. |
| -l | disabled | Replaced semicolons ';' in with line breaks in the response. |
| -v |  | Command to send to the target server. If not provided returns a default set of results. See Commands |
