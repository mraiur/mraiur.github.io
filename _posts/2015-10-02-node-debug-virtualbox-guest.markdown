---
published: true
title: Node-debug in virtualbox guest
layout: post
tags: [nodejs,debugger,javascript,port-forward,ubuntu,linux]
categories: [linux,nodejs]
permalink: /2015/11/node-debug-in-virtualbox-guest/
---
I am running a ubuntu server 15.04 guest on a windows 10 host.

To run the node-debugger( inspector ) and access if from the host.

```
node-debug -p 8888 --web-host=10.0.2.15 app.js
```

-p specify the port
--web-host change the default 127.0.0.1 host to the virtualbox network interface

Add port forwarding to the virtualbox port forwarding rules:

Name / protocol / host ip / host port / guest ip / guest port
node debugger / TCP / EMPTY / 8888 / EMPTY / 8888
