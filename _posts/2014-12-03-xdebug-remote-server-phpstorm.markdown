---
published: true
title: Xdebug on remote server and PhpStorm
layout: post
tags: [php,ide,phpstorm]
categories: [php,ide]
permalink: /2014/12/xdebug-on-remote-server-and-phpstorm/
---
Installed xdebug on remote server with this configuration:

```
zend_extension=/usr/lib/php5/20121212/xdebug.so
xdebug.remote_enable=on
xdebug.remote_handler=dbgp
xdebug.remote_host=192.168.1.200
xdebug.remote_port=9001
xdebug.remote_autostart=0
xdebug.profiler_enable = off
xdebug.profiler_enable_trigger = off
xdebug.profiler_output_name = cachegrind.out.%t.%p
```

So my "client" ip is 192.168.1.200 and just changed the port number from 9000 to 9001.

Setup of PhpStorm

Tools->DBGp Proxy-> Configuration



IDE key: YOU_CHOOSE

HOST: IP or HOST of remote server

PORT: 9001 the one we set in the remote server configuration



In File -> Settings -> PHP -> Debug



Uncheck :

Force break at the first line when no path mapping specified.

Force break at the first line when a script is outside the project.



And for the debug configuration of the project.

Run -> Edit Configuration

Add a "PHP Web Application" configuration.

Select server, if no server is in the list create one with this configuration:



Host -> server ip or domain

port : 90

Debugger: Xdebug



Also i like to check on the right top corner the "Single instance only", just not to have manually kill the debug session.

And the important part, enable the "Use path mappings ".

For each local path put a absolute remote path. Its for the debugger to know what files is the request hitting.



Starting the debugging sessions. There are two ways i found.

One is directly from

Run -> Debug "YOUR DEBUG CONFIGURATION NAME"



The other one is using a plugin for chrome or firefox to init the debugging and just attach the debugger from:

Run -> Start Listening for PHP Debug Connections



Chrome plugin: [Xdebug Helper](https://chrome.google.com/webstore/detail/xdebug-helper/eadndfjplgieldjbigjakmdgkmoaaaoc)

Firefox plugin: [he Easiest Xdebug](https://addons.mozilla.org/en-us/firefox/addon/the-easiest-xdebug/)
