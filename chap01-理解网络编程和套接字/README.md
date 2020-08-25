## 理解网络编程和套接字

### 网络编程和套接字概要

- 网络编程是编写程序使两台联网的计算机相互交换数据。
- 套接字：网络数据传输用的软件设备。
  - 接受数据的套接字
  - 发送数据的套接字

#### 构建接受数据的套接字

- 调用 `socket` 函数生成套接字

```C
#include <sys/socket.h>
int socket(int domain, int type, int protocol);
// 成功时返回文件描述符，失败时返回-1
```

&emsp;

- 调用 `bind` 函数给套接字分配地址信息（IP地址和端口号）

```C
#include <sys/socket.h>
int bind(int sockfd, struct sockaddr* myaddr, socklen_t addrlen);
// 成功返回0，失败返回-1
```

&emsp;

- 调用 `listen` 函数使得套接字转化为可接受连接状态

```C
#include <sys/socket.h>
int listen(int sockfd, int backlog);
// 成功返回0，失败返回-1
```

&emsp;

- 调用 `accept` 函数受理连接请求

```C
#include <sys/socket.h>
int accept(int sockfd, struct sockaddr* addr, socklen_t* addrlen);
// 成功返回文件描述符，失败返回-1
```



### 基于Linux的文件操作

- 文件描述符：系统分配给文件或套接字的整数。
- 3中特殊的输入输出对象：stdin、stdout、stderror，在程序执行时，自动分配文件描述符。

| 文件描述符 | 对象                      |
| ---------- | ------------------------- |
| 0          | 标准输入：Standard Input  |
| 1          | 标准输出：Standard Output |
| 2          | 标准错误：Strandard Error |

</br>

- 打开文件

```C
#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>

int open(const char* path, int flag);
// 成功时返回文件描述符，失败时返回-1
```

</br>

- 关闭文件

```C
#include <unistd.h>

int close(int fd);
// 成功时返回0， 失败时返回-1
```

</br>

- 写入文件

```C
#include <unistd.h>

ssize_t write(int fd, const void* buf, size_t nbytes);
// 成功时返回写入字节数，失败时返回-1
```

</br>

- 读取文件

```C
#include <unistd.h>

ssize_t read(int fd, void* buf, size_t nbytes);
// 成功时返回接受的字节数（遇到文件末尾返回0），失败时返回-1
```









