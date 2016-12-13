---
published: true
title: git config
layout: post
tags: [linux,git]
categories: [linux,git]
---

```
core.editor=vim
ui.colors==
alias.hist=log --pretty=format:"%h %ad | %s%d [%an]" --graph --date=short
alias.ls=log --pretty=format:%C(yellow)%h%Cred%d\ %Creset%s%Cblue\ [%cn] --decorate
color.diff=always
```