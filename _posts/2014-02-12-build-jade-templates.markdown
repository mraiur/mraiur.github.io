---
published: true
title: Build Jade Templates
layout: post
tags: [javascript,linux,sublime]
categories: [javascript,limux,windows,sublime]
permalink: /2014/02/build-jade-templates/
---
Normally its easy to build jade templates, but i work on a virtual box server ( Ubuntu server ) and my guest is Windows 7.
Using Sublime 3 with SFTP plugin works perfectly.

Added a build :
```
{
    "shell_cmd": "my_custom_build_script.bat"
}
```



Added the Putty directory to my environments PATH.
And in my_custom_build_script.bat

{% highlight bash %}
C:\"Program Files (x86)"\PuTTY\plink.exe -ssh mraiur@localhost "/PATH_TO_BUILD_SCRIPT/generate.sh"
{% endhighlight %}


On the server generate.sh is done whatever way you want it :)
