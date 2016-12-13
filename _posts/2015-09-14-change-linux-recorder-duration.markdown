---
published: true
title: Change integrated screen recorder duration time
layout: post
tags: [duration,screenrecorder,ubuntu,linux]
categories: [linux,ubuntu]
permalink: /2015/09/change-integrated-screen-recorder-duration-time/
---
I am on Ubuntu Gnome and i love the integrated screen recorder. But its duration gap is 30 sec.

To change it to 1h add.

```
gsettings set org.gnome.settings-daemon.plugins.media-keys max-screencast-length 3600
```

If you want change the value in seconds as you wish.
