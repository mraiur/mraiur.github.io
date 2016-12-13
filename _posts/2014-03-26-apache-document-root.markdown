---
published: true
title: Apache change DocumentRoot
layout: post
tags: [linux,apache]
categories: [linux]
permalink: /2014/03/apache-change-documentroot/
---
Every time i forget what has to be done to stop with the "Forbidden" page after i change the Root directory.
So first add the user you use to add/update/delete your files to www-data group.

```
usermod -a -G www-data mraiur
```


Update permissions of file that must be writable by www-data and the user

```
chmod 0775 FILE
```

Then in the 000-default in /etc/apache2/sites-available put :

```
DocumentRoot /NEW_PATH
<Directory "/NEW_PATH">
    Options Indexes FollowSymLinks
    AllowOverride None
    Require all granted
    Order allow,deny
    Allow from all
</Directory>
```
