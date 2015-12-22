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