---
title: Lsky Pro图床迁移注意
date: 2021-09-14 21:21:48
tags:
---

一键LNMP环境，迁移图床
编辑文件最后一行，注释掉
```
/usr/local/nginx/conf/fastcgi.conf
```

编辑文件显示调试日志
```
php_admin_value[error_log] = /usr/local/php/var/log/php_errors.log
php_admin_flag[log_errors] = on
```


