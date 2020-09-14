cmake_minimum_required(VERSION 3.14)
project(TCP_IP C)

set(CMAKE_C_STANDARD 99)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY bin/ )

# chapter 01 理解网络编程和套接字
add_executable(helloserver chap01-理解网络编程和套接字/hello_server.c)
add_executable(helloClient chap01-理解网络编程和套接字/hello_client.c)
add_executable(lowOpen chap01-理解网络编程和套接字/low_open.c)
add_executable(lowRead chap01-理解网络编程和套接字/low_read.c)

# chapter 02 套接字类型与协议设置
add_executable(tcpClient chap02-套接字类型与协议设置/tcp_client.c)
add_executable(tcpServer chap02-套接字类型与协议设置/tcp_server.c)

# chapter 04 基于TCP的服务器端与客户端
add_executable(echo_server "chap04-基于TCP的服务器端与客户端(1)/echo_server.c")
add_executable(echo_client "chap04-基于TCP的服务器端与客户端(1)/echo_client.c")
add_executable(tcp_client "chap04-基于TCP的服务器端与客户端(1)/tcp_client.c")
add_executable(tcp_server "chap04-基于TCP的服务器端与客户端(1)/tcp_server.c")