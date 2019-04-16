---
title: python tcp
date: 2019-04-02 14:59:09
tags: 网络
categories: python
---

## TCP

### tcp_client.py

```python
import socket
import threading
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
# 建立连接:
s.connect(('127.0.0.1', 10000))
# 接收欢迎消息:
print(s.recv(1024).decode('utf-8'))
for data in [b'Michael', b'Tracy', b'Sarah']:
    # 发送数据:
    s.send(data)
    print(s.recv(1024).decode('utf-8'))
s.send(b'exit')
s.close()
```

### tcp_server.py

```python
import socket,os
import threading
import time
s=socket.socket(socket.AF_INET,socket.SOCK_STREAM) #创建连接
s.bind(('127.0.0.1',10000))　#设置服务器端口,小于1024的端口需要权限
s.listen(3) #设置连接数限制
print('等待连接...')


def tcplink(sock, addr):
    print('Accept new connection from %s:%s...' % addr)
    sock.send(b'Welcome!')
    while True:
        data = sock.recv(1024)
        time.sleep(1)
        if not data or data.decode('utf-8') == 'exit':
            break
        sock.send(('Hello, %s!' % data.decode('utf-8')).encode('utf-8'))
    sock.close()
    print('Connection from %s:%s closed.' % addr)

while True:
    sock ,addr=s.accept()
    t=threading.Thread(target=tcplink,args=(sock,addr))
    t.start()
```

## UDP

### udp_client.py

```python
import socket

s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
for data in [b'Michael', b'Tracy', b'Sarah']:
    # 发送数据:
    s.sendto(data, ('127.0.0.1', 9999))
    # 接收数据:
    print(s.recv(1024).decode('utf-8'))
s.close()
```

### udp_server.py

```python
import socket,os
import threading
import time

s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
# 绑定端口:
s.bind(('127.0.0.1', 9999))
print('waiting for connecting..')

while True:
    # 接收数据:
    data, addr = s.recvfrom(1024)
    print('Received from %s:%s.' % addr)
    s.sendto(b'Hello, %s!' % data, addr)
```

