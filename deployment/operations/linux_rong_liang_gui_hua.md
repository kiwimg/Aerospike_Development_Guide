# Linux 容量规划

 Aerospike Database——你可以通过收集需求计算您的硬件大小。然后,取决于你想要一个内存数据库,还是一个混合SSD /内存数据库,或者一个Amazon EC2(云)数据库,

## 计算总存储、内存和吞吐量

### 数据存储要求

存储为一个record的总和
>```64 bytes```

如果使用一个set名称：

>```+ 9 bytes 开销 + set 名称 length```

每个bin的一般开销：

>```+ 28 bytes```

每个bin的类型开销

>```+ 2 bytes for integer data, 5 bytes for string or blob data```

数据本身大小

>```+ data size```



这导致存储大小应该围捕了128字节的倍数。例如,存储记录一本包含一个整数,用一组名字10个字符长,我们需要:
由此产生的存储大小应为128字节的倍数。例如，用一个bin包含一个整数类型存储record，set名10个字符长，我们需要：

>```64 + (9 + 10) + 28 + (2 + 8) = 121 -> rounded up = 128 bytes (1 block)```

### 内存需求