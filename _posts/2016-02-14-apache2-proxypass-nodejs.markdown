---
published: true
title: Apache2 proxy pass to nodejs app
layout: post
tags: [linux,ubuntu,apache2,forward,proxy,port,port-forward]
categories: [linux,ubuntu]
permalink: /2016/02/apache2-proxy-pass-to-nodejs-app/
---
Enable proxy modules:

```
a2enmod proxy
a2enmod proxy_http
```

Setup the vhost. I like to name my project for dev like this
VHOSTNAME.dev

```
<VirtualHost *:80<
	ServerName VHOSTNAME.dev
	ServerAdmin webmaster@localhost
	ProxyPass / http://localhost:3000/
	#LogLevel info ssl:warn

	ErrorLog ${APACHE_LOG_DIR}/VHOSTNAME-error.log
	CustomLog ${APACHE_LOG_DIR}/VHOSTNAME-access.log combined

</VirtualHost<
```

And the most easy way to link the VHOSTNAME.dev i add a line in
**/etc/hosts**

127.0.0.1 VHOSTNAME.dev
