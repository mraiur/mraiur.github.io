---
published: true
title: xdebug with sumblime windows host to linux server
layout: post
tags: [debug,ide,sublime,sublime-text,windows-to-linux,xdebug]
categories: [linux,window,sublime,ide]
permalink: /2014/06/xdebug-with-sumblime-windows-host-to-linux-server/
---
When you write code normally its on a dev server and not on your machine.

My case home/work is Windows + Sublime Text 3 (client) and Ubuntu Server (remote server).

To make it work especially with SFTP plugin change your project configuration file like:

```
{
	"folders":
	[
		{
			"follow_symlinks": true,
			"path": "E:\\projects\\xdebug"
		}
	],
    "settings" : {
        "xdebug": {
            "path_mapping": {
                "[REMOTE PROJECT PATH]/xdebug.php": "E:/projects/xdebug/xdebug.php"
            },
            "url": "http://YOUR_REMOTE_DEV_SERVER/xdebug.php",
            "super_globals": true,
            "close_on_stop": true
        }
    }
}
```

xdebug.php is not mandatory to be in the path or the url was just put for the test.

That is not all, by default the xdebug port is 9000 for some reason it didn't work on that port.
Will investigate latter.
Xdebug php.ini configuration:

```
zend_extension=PATH_TO_EXTENSION/xdebug.so
xdebug.default_value = 1
xdebug.remote_enable = 1
xdebug.remote_autostart = 0
xdebug.remote_port = 9900
xdebug.remote_handler = dbgp
xdebug.remote_host= YOUR_CLIENT_IP
```

I know i can debug with Netbeans, Aptana or something more "IDE" but i love sublimes simplicity and speed.

Here is the plugin: [Xdebug Client](https://sublime.wbond.net/packages/Xdebug%20Client)

Open the url of the project and paste at the end of the url:

```
?XDEBUG_SESSION_START=sublime.xdebug
```
