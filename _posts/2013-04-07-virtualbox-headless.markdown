---
published: true
title: VirtualBox - headless
layout: post
tags: [windows,virtualbox]
categories: [windows,virtualbox]
permalink: /2013/04/virtualbox-headless/
---
I don't have linux on my desktop machine but i do most of the work at home with it. But i don't like the windows solution for working with php and git so VirtualBox-Headless linux server.

Install a low resource linux( my case ubuntu-server) server on a  new virtualbox image with name for example "ubuntu-server".

Then i created two shortcuts.

1. ubuntu-server-start

2. ubuntu-server-stop


For ubuntu-server-start shortcut in <strong>Target</strong> put :

{% highlight bash %}
C:\Program Files\Oracle\VirtualBox\VBoxManage.exe" startvm ubuntu-server --type headless
{% endhighlight %}


For ubuntu-server-stop shortcut in **Target** put:

{% highlight bash %}
"C:\Program Files\Oracle\VirtualBox\VBoxManage.exe" controlvm ubuntu-server savestate
{% endhighlight %}


If you made the virtual image with different name just change it in:

{% highlight bash %}
"C:\Program Files\Oracle\VirtualBox\VBoxManage.exe" startvm **ubuntu-server** --type headless
{% endhighlight %}

{% highlight bash %}
"C:\Program Files\Oracle\VirtualBox\VBoxManage.exe" controlvm **ubuntu-server** savestate
{% endhighlight %}
