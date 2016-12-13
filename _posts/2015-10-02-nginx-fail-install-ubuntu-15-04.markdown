---
published: true
title: nginx fails to install on ubuntu server 15.04
layout: post
tags: [nginx,install,fail,ubuntu 15.04,ubuntu,linux]
categories: [linux,ubuntu]
permalink: /2015/11/nginx-fails-to-install-on-ubuntu-server-15-04/
---
So the problem is that the dependencies cannot resolve property.
And after an hour of failing to install it the solution i came up is this.
You have to install in this order the packages:


```
sudo apt-get install nginx-common=1.6.2-5ubuntu3.1
sudo apt-get install nginx-core=1.6.2-5ubuntu3.1
sudo apt-get install nginx1.6.2-5ubuntu3.1
```

And nginx light up after that.
