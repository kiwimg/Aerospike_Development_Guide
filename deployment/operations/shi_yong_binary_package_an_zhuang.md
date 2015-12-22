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