---
published: true
title: Multi-size style refresh
layout: post
tags: [code,javascript,nodejs]
categories: [javascript,nodejs]
permalink: /2013/09/multi-size-style-refresh/
---
[![IMAGE ALT TEXT HERE](https://img.youtube.com/vi/y2dimu3FDp8/0.jpg)](https://www.youtube.com/watch?v=y2dimu3FDp8)

I started looking a easy way to test multiple resolution tests. So my current solution.
1. Nodejs server
Running a simple websocket server
2. Start-Stop server bash script
3. A refresher page.
Used when opened to broadcast a major refresh signal.
4. Custom sublime builder command
5. A simple snippet for the current page that's under development

1 - Server
Must be visible to all browsers + Editor machine

```
"use strict";
// used for start-stop script
process.title = 'nodejscurrent';

var app = require('http').createServer(handler),
	io = require('socket.io').listen(app),
  	fs = require('fs');

app.listen(7777);

function handler (req, res) {
  fs.readFile(__dirname + '/index.html',
  function (err, data) {
    if (err) {
      res.writeHead(500);
      return res.end('Error loading index.html');
    }

    res.writeHead(200);
    res.end(data);
  });
}

io.sockets.on('connection', function (socket) {
	socket.on('do-refresh', function (data) {
		socket.broadcast.emit('refresh');
	});

	io.sockets.on('message', function(data) {
		console.log("MSG", data);
	});
});
```

2. Start-Stop bash script

```
#!/bin/bash
ps aux | grep nodejsrefresher | awk '{ system("kill -9 "$2)}'; nodejs server.js
```

3. The refresher page.
Must be visible for the sublime-editor

```

		<!-- REFRESHER -->
<script type="text/javascript" src="http://static/socket/socket.io.min.js"></script><script type="text/javascript">// <![CDATA[
		  var socket = io.connect('http://localhost:7777');
		  socket.on('connect', function (data) {
		  		socket.emit('do-refresh', { my: 'data' });
				window.close();
		  });

// ]]></script>
 <!-- END -->
```

4. Custom sublime builder command
* Create from Tools -> Build System -> New Build System

```
{
	"shell_cmd": "google-chrome http://REFRESHER-VISIBLE-URL/refresh.html"
}
```

5. A simple snippet for the current page that's under development
Add in head section. Put the client socket.io.min.js for example in 'static' folder.

```
<!-- REFRESHER -->
<script type="text/javascript" src="http://VISIBLE_URL/socket.io.min.js"></script><script type="text/javascript">// <![CDATA[
$(document).ready(function(){
	var socket = io.connect('http://IP_OF_THE_SERVER_MACHINE:7777');
		socket.on('refresh', function (data) {
		window.location = "?rnd="+Math.random();
	});
})
// ]]></script>
<!-- END -->
```

Maybe not a perfect solution but works really good for many browser windows + devices.
Added in chrome "responsiView" plugin for testing standard resolutions.
