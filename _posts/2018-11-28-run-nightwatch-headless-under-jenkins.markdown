---
published: true
title: Run nightwatch.js headless under jenkins
layout: post
tags: [jenkins,nightwatch.js,headless]
categories: [ci]
permalink: /run-nightwatch-headless-under-jenkins
---

I had a problem with running headless chrome tests with nightwatch.js under jenkins.
The jenkins server is serving the site to be tested with apache2.
But headless chrome is ignoring /etc/hosts file.
Setting *--no-proxy-server* is ignored IF running in headless mode.

Here are the versions of the packages:

```

    xvfb - 2:1.19.6-1ubuntu4.2
    google-chrome - 70.0.3538.110
    jenkins - 2.138.3
    nightwatch - v0.9.21
    Ubuntu 18.04 
```

Also the jenkins user is set in sudoers file:

```

jenkins ALL=(ALL) NOPASSWD:/usr/sbin/service apache2 *
jenkins ALL=(ALL) NOPASSWD:/usr/sbin/service php*-fpm *
jenkins ALL=(ALL) NOPASSWD:/usr/bin/google-chrome
jenkins ALL=(ALL) NOPASSWD:/bin/chmod 775 -R /var/lib/jenkins/workspace 
jenkins ALL=(ALL) NOPASSWD:/bin/chown /var/lib/jenkins/workspace

```

Before running the nightwach.js tests the jenkins user must start a Xvfb like:

```

Xvfb :10 &
export DISPLAY=:10

```

Or run the tests with xvfb-run


```

xvfb-run nightwatch

```


Tips for debugging:
- Tail the custom application log if it has any. I was testing a laravel project and tailing storage/logs/laravel.log Its a good idea to truncate the file if the projects is not deleted before each jenkins build.
- Tail ALL logs of nginx/apache to be sure you hit the server
- Test nightwach url to open google.com and take a screenshot

```

browser
    .url('https://google.com')
    .saveScreenshot('./reports/homepage.png')

```
- Enable source output in nightwach 

```

browser
    .url('https://google.com')
    .source((result) => {
        // Source will be stored in result.value
        console.log(result.value);
    })
```
