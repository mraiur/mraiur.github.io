---
published: true
title: nginx + php-fpm
layout: post
tags: [php,ubuntu,nginx,php-fpm]
categories: [php,nginx,ubuntu]
permalink: /2015/06/nginx-php-fpm/
---
In the nginx config file( on ubuntu its /etc/nginx/nginx.conf )

```
 server{
    listen  80;
    autoindex on;
    server_name project.dev
    root /home/mraiur/work;
    location ~ \.php$ {
        fastcgi_split_path_info ^(.+\.php)(/.+)$;
        fastcgi_pass 127.0.0.1:9000;
        fastcgi_index index.php;
        include fastcgi_params;
        fastcgi_param SCRIPT_FILENAME $document_root/$fastcgi_script_name;
    }
}
```

Also we need to configure the php-fpm to serve on port 9000.
We set it in the www.conf ( on ubuntu its in /etc/php5/fpm/pool.d/www.conf )

```
;listen = /var/run/php5-fpm.sock
listen = 127.0.0.1:9000

listen.owner = www-data
listen.group = www-data
listen.mode = 0660
```

Also because they are two different servers after the config changes we must restart:

For fpm config restart:

```
sudo service restart php5-fpm
```

For nginx config restart:

```
sudo service restart nginx
```
