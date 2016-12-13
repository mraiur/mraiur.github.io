---
published: true
title: MySQL execution logging
layout: post
tags: [linux,git]
categories: [linux,mysql]
---
[mk-query-digest](http://www.maatkit.org/doc/)

```
netstat -na | grep 6070
ssh -f -N -L 6070:192.168.9.101:3306 mraiur@127.0.0.1
sudo tcpdump -s 65535 -x -nn -q -tttt -i any -c 1000 port 6070    > mysql.tcp.txt
./mk-query-digest --type tcpdump --limit 15 --timeline --watch-server 127.0.0.1:6070 mysql.tcp.txt > DDLOG.txt
```


```
sudo tcpdump -s 65535 -x -nn -q -tttt -i any -c 1000 port 9377 > calcTest
```


```
./mk-query-digest --type tcpdump --limit 15 --timeline --watch-server 127.0.0.1:9377  calcOpenTest  > calcOpen.txt
```


```
127.0.0.1:6070
```