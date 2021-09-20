---
title: 关闭MySQL的DNS反向解析(unauthenticated user 解决办法)
date: 2021-09-20 22:09:11
tags:
---

mysql默认状态下是会自动反向解析,如果我们处理不好使用show processlist查看是会发现进行中有大量的unauthenticated user提示，下面我来给大家介绍解决unauthenticated user的方法。

例如

```
More Actionsmysql>show processlist;| 20681949 | unauthenticated user | A.B.C.D:52497 | NULL | Connect | | Reading from net | NULL |  | 20681948 | unauthenticated user | W.X.Y.Z:52495 | NULL | Connect | | Reading from net | NULL |
```

发现有非常多的 unauthenticated user 尝试做登入使用 mysql的情况，当这种情况无限制发生时就会造成系统十分缓慢。

查阅mysql官方网站得知，这属于官方一个系统上的特殊设定，就把他当成mysql的一个bug算了。不管链接的的方式是经过 hosts 或是 IP 的模式，他都会对 DNS 做反查 mysqld 会尝试去反查 IP -> dns，由于反查解析过慢，就会无法应付过量的查询。

如果处于公网上的MySQL出现大量的非法用户尝试登陆的情况，给服务器带来的负荷是不可想像的。

**解决办法：**

一、执行：

```
# /usr/local/mysql/bin/mysqld_safe --skip-name-resolve --user=mysql&
```

二、修改MySQL的配置文件my.cnf，追加：

```
[mysqld] skip-name-resolve
```

