---
published: true
title: VirtualBox Win(host) - Linux(guest) samba share
layout: post
tags: [linux,windows,samba,share,virtual]
categories: [linux,samba,windows]
permalink: /2015/08/virtualbox-winhost-linuxguest-samba-share/
---
I love linux mainly because i can work natively.

Using the samba share instead of the virtual box share is that.
- Samba share is much faster then the virtual box share.
- Samba share is not messing the ownership and permission of the files/directories.

To have something similar on Windows my solution is :

Windows Host to mount a samba share from Linux (guest).

Virtual box setup for the VM.
Network adapters:
1. NAT (Default)
2. Host-Only adapter
Advanced-> Premiscuos Mode ( Allow all )

Host-only adapter creates a network interface in the windows machine.
Change IP4 settings to :
- Obtain an IP address automatically
- Obtain DNS server address automatically

On the VM make sure you have enabled eth0 ( NAT ) and eth1 ( Host-Only adapter ).
/etc/network/interfaces

```
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
```

For the samba share. Its not the best solution but this way its most "native".
/etc/samba/smbd.conf
More information for [socket options](https://calomel.org/samba_optimize.html)

```
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=65536 SO_SNDBUF=65536

[root]
  path = /
  writable = yes
  guest ok = yes
  valid users = mraiur
  force user = mraiur
  force group = www-data
  create mode = 0644
  directory mode = 0755
  share modes = yes
```

Also because samba is a different service you should add a user ( admin and force user in the cfg );

```
smbpasswd -a mraiur
```

-a adds a new user if a user exists without -a will change the samba share password.
