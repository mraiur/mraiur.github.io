---
published: true
title: Simple keypress count under linux
layout: post
tags: [linux,ubuntu,tools,keypress,keypress-count]
categories: [linux,ubuntu,tools]
permalink: /2016/01/simple-keypress-count-under-linux/
---
First check where is your keyboard mounted:

```
cat /var/log/Xorg.0.log | grep keyboard
```

For me its something like
(II) evdev: ROCCAT ROCCAT Ryos MK Glow: Configuring as keyboard

Next pipe the output to a file and after count the "words";

In one terminal where 2 is i guess (II) from the cat above :

```
cat /dev/input/event2 ~/keyboard.txt
```

And count the keypresses with:

```
echo $(( $(cat ~/keyboard.txt | wc -c) / 96))
```


A complete Gui tool : [WhatPulse](http://whatpulse.org/)
