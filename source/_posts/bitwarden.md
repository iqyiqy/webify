---
title: Bitwarden密码服务搭建
date: 2021-09-17 22:01:15
tags:
---

开源密码管理器Bitwarden。在GitHub上有个项目叫做 bitwarden_rs，并且提供了 Docker 镜像。对机器配置的要求很低，而且 Docker 镜像体积很小，部署非常方便。

主要步骤：
1. 启动主程序
```
docker run -d --name bitwarden \
    -e SIGNUPS_ALLOWED=true \
    -p 8090:80 \
    -v /home/data/bitwarden/:/data/ \
    bitwardenrs/server:latest
```
2. nginx反向代理
略
