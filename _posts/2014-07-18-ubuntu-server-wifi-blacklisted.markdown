---
published: true
title: ubuntu server. WiFi disabled on boot
layout: post
tags: [linux,ubuntu,wifi,blacklisted]
categories: [linux,ubuntu]
permalink: /2014/07/ubuntu-server-wifi-disabled-on-boot/
---
I have a problem on a laptop running Ubuntu Server 14.04 that the wifi is software blocked on boot.
I know its a ugly fix, but its fixed.

```
#!/bin/sh
echo "-> ifdown wlan0"
ifdown wlan0
echo "-> ifconfig eth0 down"
ifconfig eth0 down
echo "-> rfkill unblock all"
rfkill unblock all
echo "-> iwconfig wlan0 power on"
iwconfig wlan0 power on
echo "-> ifup wlan0"
ifup wlan0
echo "-> dhclient wlan0"
dhclient wlan0
echo "-> ifup wlan0"
ifup wlan0
```
