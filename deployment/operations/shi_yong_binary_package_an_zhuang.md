# 使用Binary Package安装


```ruby
wget -O aerospike.tgz 'http://aerospike.com/download/server/latest/artifact/tgz'
tar -xvf aerospike.tgz
cd aerospike-server
./bin/aerospike init
sudo ./bin/aerospike start && \
sudo tail -f ./var/log/aerospike/aerospike.log | grep cake
# wait for it. "service ready: soon there will be cake!"
```

## Overview

本教程安装的aerospike使用Linux的glibc 2.11或以上版本。glibc 2.11发布2009年1月,和大多数的Linux发行版——Debian 6 +,Centos 6 + 12 + OpenSUSE,Ubuntu 10.04 +支持这个版本

这个包包含一个aerospike二进制安装包可以运行在一个没有安装其他软件的用户目录,并且不需要root权限

## Download Aerospike

如果您已经下载到服务器,您可以跳过此步骤。

>1. 下载aerospike  Community Edition

>```wget -O aerospike.tgz 'http://aerospike.com/download/server/latest/artifact/tgz'```


有关发布的详细访问该[下载页](http://www.aerospike.com/download)。


## Install Aerospike
如果已经在服务器安装过，可以跳过此步骤，启动aerospike