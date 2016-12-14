---
published: true
title: Fix ttf-mscorefonts install bug
layout: post
tags: [linux,tools,ubuntu,fix,ttf-mscorefonts]
categories: [linux,ubuntu]
permalink: /2016/12/14/ttf-mscorefonts
---

There is a problem in ubuntu 16.10 ( gnome ) that after login the tts-mscorefonts installer pops propting to "install" the missing packages.
The problems is that there are missing links for downloading **andale32.exe**.
First there was other solutions that repared the missing other fonts except andale32.

# The simplest was to re-install the package.

```
sudo apt purge ttf-mscorefonts-installer
sudo apt install ttf-mscorefonts-installer
```

I like to purge and install instead of "reinstall" option.

# At the end i found a post pointing that the best way is to download the deb package from debian.

[Download deb](https://packages.debian.org/en/sid/all/ttf-mscorefonts-installer/download)

