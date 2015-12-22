# 命令 asmonitor - Commands


### help



显示用法信息 Display usage information

>```Monitor> help```


### info

>```Monitor> info [<table>] [-h <host>[:<port>][, ...]] [-p <port>]```


## asinfo

>```Monitor> asinfo [-v <value>] [-h <host>[:<port>][, ...]] [-p <port>]```


### stat

>```Monitor> stat [-v <value>] [-h <host>[:<port>][, ...]] [-p <port>]```


### compareconfig

>``` Monitor> compareconfig [-h <host>[:<port>][, ...]] [-p <port>]```

### checkmem

>```Monitor> checkmem```

### latency

> ```Monitor> latency [-h <host>[:<port>][, ...]] [-p <port>]
                 [-v <filter>] [-k (reads | writes_master | writes | writes_reply | proxy)]
                 [-d <seconds>] [-b <seconds>] [-s <seconds>]
                 [-t] [-m] [-c]```

### watch

>```Monitor> watch -n <seconds> <command>```

### add

>```Monitor> add -h <host>[:<port>][, <host>[:<port>] [, ...]] [-p <port>]```

### remove

>```Monitor> remove -h <host>[:<port>][,...] [-p <port>]```


### edittable

>```Monitor> edittable```


### sorttable

>```Monitor> sorttable```

### restoredefault

> ```Monitor> restoredefaults```


### exit

>```Monitor> exit```