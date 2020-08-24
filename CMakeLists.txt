cmake_minimum_required(VERSION 3.14)
project(TCP_IP C)

set(CMAKE_C_STANDARD 99)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY bin/ )

add_executable(helloserver chap01-理解网络编程和套接字/hello_server.c)
add_executable(helloClient chap01-理解网络编程和套接字/hello_client.c)