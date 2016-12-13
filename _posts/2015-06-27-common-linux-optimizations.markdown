---
published: true
title: Common Optimizations
layout: post
tags: [linux,speedup,optimize,ubuntu]
categories: [linux,speedup,optimize,ubuntu]
permalink: /2015/06/common-optimizations/
---
I will update this post with common linux optimization tricks.

### VM.SWAPPINESS

The most useful one is the vm.swappiness configuration. If you have enough RAM 4GB/8GB/16GB decreasing this value will use more RAM but will not flush active pages to the HDD.
This is most noticeable boost when your HDD is not SSD.

To check the current value:
```
sudo sysctl -a | grep vm.swappiness
```

To reload changes:
```
sudo sysctl -p
```

The default is around 60 and i normally decrease it to <strong>10</strong>:
```
sudo vim /etc/sysctl.conf
```

If you dont find this property to be changed <strong>vm.swappiness</strong> just add it at the bottom of the file:
```
vm.swappiness = 10
```

Increase number of incoming connections from 100 to 65536
```
net.core.somaxconn = 32768
```

Increase number of incoming connections backlog
```
net.core.netdev_max_backlog = 65536
```

Maximum Socket Receive Buffer
```
net.core.rmem_max = 12582912
```

Maximum Socket Send Buffer
```
net.core.wmem_max = 12582912
```

Increase the write-buffer-space allocatable
```
net.ipv4.tcp_wmem = 8192 65536 16777216
net.ipv4.udp_wmem_min = 16384
```

Increase the read-buffer space allocatable
```
net.ipv4.tcp_rmem = 8192 87380 16777216
net.ipv4.udp_rmem_min = 16384
```

Increase the tcp-time-wait buckets pool size to prevent simple DOS attacks
```
net.ipv4.tcp_max_tw_buckets = 1440000
net.ipv4.tcp_tw_recycle = 1
net.ipv4.tcp_tw_reuse = 1
```

For no SSD computers currently i am trying this:

```
vm.vfs_cache_pressure = 50
vm.dirty_background_ratio = 50
vm.min_free_kbytes = 503316 # ~ 5-6% of physical memory   
vm.swappiness = 5
vm.dirty_ratio = 80
```

Enable HugePage size [Ubuntu KVM](https://help.ubuntu.com/community/KVM%20-%20Using%20Hugepages):

```
# Allocate 256 HugePageTables (start with a low number but increas it before using it)                                                                                                                             
vm.nr_hugepages = 256    
```
