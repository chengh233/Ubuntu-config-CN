# Ubuntu-config-CN
how to set development environment in mainland China

*System: Ubuntu 20.04 LTS*

*wsl: Windows Subsystem for Linux*

*Terminal: Windows terminal*

## Issue #1: Cannot ping www.baidu.com

```
vim /etc/resolv.conf 
```
modify
```
nameserver 8.8.8.8
```

## Issue #2: Get apt
```
sudo vim /etc/apt/sources.list
```
Modify
```
# 默认注释了源码镜像以提高 apt update 速度，如有需要可自行取消注释
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-updates main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-updates main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-backports main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-backports main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-security main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-security main restricted universe multiverse
```

## Issue #3: Getting github
Using Ipaddress.com to find following ip address
```
1. github.com
2. assets-cdn.github.com
3. github.global.ssl.fastly.net
```
Add following codes at the end of
```
Windows: c/windows/system32/drivers/etc/hosts
Ubuntu 20.04: /etc/hosts
```
Content
```
192.30.253.112 github.com
151.101.184.133 assets-cdn.github.com
151.101.185.194 github.global.ssl.fastly.net
```
Install network-manager
```
sudo apt install network-manager
```
Refresh network
```
sudo service network-manager restart
```

## Issue #4: Cannot get proxy.golang.org

```
go env -w GOPROXY=https://goproxy.cn
```
