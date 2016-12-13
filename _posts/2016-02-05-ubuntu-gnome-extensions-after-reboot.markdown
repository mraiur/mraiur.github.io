---
published: true
title: Ubuntu Gnome extensions not enabled after reboot fix
layout: post
tags: [linux,ubuntu,extensions,gnome-shell]
categories: [linux,ubuntu]
permalink: /2016/02/ubuntu-gnome-extensions-not-enabled-after-reboot-fix/
---
The most common solution for the problem when you reboot all your extensions are disabled.

First you after you enabled them in the terminal type:

```
gsettings get org.gnome.shell enabled-extensions
```


## Example output

{% highlight bash %}
['alternate-tab@gnome-shell-extensions.gcampax.github.com', 'unitylike-hotkey@webgyerek.net', 'impatience@gfxmonk.net', 'topIcons@adel.gadllah@gmail.com', 'user-theme@gnome-shell-extensions.gcampax.github.com', 'workspace-indicator@gnome-shell-extensions.gcampax.github.com']
{% endhighlight %}

Create a .sh script, i create it in my home folder with name ".extensions.sh" the dot makes it hidden file in nautilus.
Thats only if your nautilus preferences is set not to show hidden files.

Put in this .extensions.sh file between the double quotes the output of the previous command.

```
gsettings set org.gnome.shell enabled-extensions ""
```

## Example


{% highlight bash %}
gsettings set org.gnome.shell enabled-extensions "['alternate-tab@gnome-shell-extensions.gcampax.github.com', 'unitylike-hotkey@webgyerek.net', 'impatience@gfxmonk.net', 'topIcons@adel.gadllah@gmail.com', 'user-theme@gnome-shell-extensions.gcampax.github.com', 'workspace-indicator@gnome-shell-extensions.gcampax.github.com']"
{% endhighlight %}

And in startup applications add this script.

This way after reboot the script will set your enabled extensions.
The only problem is that you have to update it on new or removing extensions.
