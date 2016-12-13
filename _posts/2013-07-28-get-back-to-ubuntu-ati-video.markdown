---
published: true
title: get back to ubuntu ATI video card install
layout: post
tags: [ati,hd-7750,linux,ubuntu]
categories: [linux,ubuntu]
permalink: /2013/07/get-back-to-ubuntu-ati-video-card-install/
---
I had ubuntu ( no dual boot ) on my laptop. With no hard to install driver problems. Decided to to install it also on the desktop( the real user machine ). I have dual monitor setup but with the default drivers i have split view, but no GPU acceleration. With the "suggested"  drivers i had GPU acceleration but no split view, only mirror view. So how to fix this.

1. Install Ubuntu 13.04

2. Update software **AND** **dont select any additional drivers**.

3. Install ATI's official drivers ( download zip, unrar, execute .run file,

3.1 Download Arhive

3.2 Unrar

3.3 chmod +x .run file

3.4 Run the script ( sudo ./*.run )

3.5 NEXT->NEXT->NEXT

3.6 Reboot

4. run in the terminal: **amdcccle**

5. Select your dual-split view settings, this will be only from the catalyst menu
