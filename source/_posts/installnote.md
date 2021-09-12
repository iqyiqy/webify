---
title: 搭建为知笔记
date: 2021-09-12 23:44:44
tags:
---

- docker需要服务器空闲内存大于1G
具体过程：https://www.wiz.cn/zh-cn/docker
主要步骤：
1. 启动主程序
docker run --name wiz --restart=always -it -d -v  /home/wizdata:/wiz/storage -v  /etc/localtime:/etc/localtime -p 8980:80 -p 9269:9269/udp  wiznote/wizserver
2. nginx反向代理
docker run -d --name nginx -p 80:80 -p 443:443 -v /etc/nginx/vhost:/etc/nginx/conf.d nginx
