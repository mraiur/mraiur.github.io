---
published: true
title: Extract gnome-shell gjs files from .so file
layout: post
tags: [gjs,javascript,linux,extract]
categories: [linux,javascript]
permalink: /2015/06/extract-gnome-shell-gjs-files-from-so-file/
---
Extract Gnome JS classes from libgnome-shell.so file:

This will export each class in export directory.


```
! /bin/sh

gs=/usr/lib/gnome-shell/libgnome-shell.so

rm -rf export;

for r in `gresource list $gs`; do

   exportPath=&quot;export/&quot;${r#\/org\/gnome\/shell\/}

   fileName=$(basename $exportPath);

   exportDir=$(dirname $exportPath);

   mkdir -p $exportDir;

   gresource extract $gs $r &gt; $exportPath;

done
```
