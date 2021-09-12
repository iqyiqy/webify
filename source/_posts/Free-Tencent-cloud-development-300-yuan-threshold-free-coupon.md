---
title: Docker安装
date: 2021-09-12 21:44:44
tags:
---



安装docker
```
wget -qO- https://get.docker.com | sh
```

安装docker-compose
```
curl -L https://github.com/docker/compose/releases/download/1.25.4/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
```

通过修改daemon配置文件/etc/docker/daemon.json来使用加速器。
```
{
    "registry-mirrors": ["https://e1c0f65ef3f243c39ff28782fa87b034.mirror.swr.myhuaweicloud.com"]
}
```



