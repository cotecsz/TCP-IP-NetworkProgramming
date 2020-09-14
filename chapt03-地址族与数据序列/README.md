## 地址族与数据序列

#### 分配给套接字的IP地址与端口号

- IP（Internet Protocol）为收发网络数据而分配给计算机的值。

#### 网络地址

- IP地址分为网络地址和主机地址，分为A、B、C、D、E等类型。
  - A类地址：0～127，以0开头
  - B类地址：128～191，以10开头
  - C类地址：192～223，以110开头

</br>

#### 端口号

- IP地址用于区分计算机，端口号用于区分计算机中的应用程序。
- 端口号由同一操作系统内区分不同套接字设置，16位
  - 可分配端口号范围：0～65535
  - 知名端口号：0～1023，分配给特定应用程序

</br>

### 地址信息表示

- 地址信息结构体

```C
struct sockaddr_in{
  	sa_family_t			sin_family;		// 地址族
  	uint16_t 				sin_prot;			// 16位TCP/UDP端口号
  	struct in_addr	sin_addr;			// 32位IP地址
  	char						sin_zero[8];	// 填充0
}
```

- 其中，`in_addr` 定义

```C
struct in_addr{
  	in_addr_t				s_addr;				// 32位IPv4地址
}
```

</br>

#### 成员`sin_family`：协议族

- 协议族，IPv4使用4字节地址族，IPv6使用16字节地址族

#### 成员 `sin_port`：端口号

- 保存16位端口号，以网络字节序保存

#### 成员 `sin_addr` ：IP地址

- 保存32位IP地址信息，以网络字节序保存。结构体 `in_addr` 声明为 `uint32_t` ,可以当作32为整数。

#### 成员 `sin_zero` ：填充0

- 为使结构体 `sockaddr_in` 的大小与 bind参数 `sockaddr` 结构体保持一致而插入的成员。

```C
struct sockaddr_in serv_addr;
...
if (bind(serv_sock, (struct sockaddr* ) &serv_addr, sizeof(serv_addr)) == -1)
  	error_handling("bind() error");
...
```

</br>

```C
struct sockaddr{	
		sa_family_t		sin_family;			// 地址族
  	char					sa_data[14];		// 地址信息
}
```

- `sa_data` 保存的地址信息包含IP地址和端口号，剩余部分填充0
- `struct sockaddr` 与 `struct sockaddr_in` 大小相同，将 `sockaddr_in` 强制转换为 `sockaddr` 。

<br>



### 网络字节序与地址变换

#### 字节序

- 大端序：高位字节存放在低位地址
- 小端序：高位字节存放在高位地址
- 网络字节序统一为大端序。

</br>









































