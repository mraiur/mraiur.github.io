---
published: true
title: Caps lock to ESC
layout: post
tags: [linux,tools,vim,esc,caps lock]
categories: [linux,tools,vim]
permalink: /2015/12/caps-lock-to-esc/
---
Trying to learn to work with VIM and pressing escape is not the most easy to reach button.
So most people bind CapsLock to ESC, because its not used 99.9999% of the time.

First get your current keyboard option settings:

```
dconf read /org/gnome/desktop/input-sources/xkb-options
```

# Example output

```
['grp_led:scroll', 'numpad:microsoft', 'grp:win_space_toggle']
```

So we need to add <b>'caps:escape'</b>

```
dconf write /org/gnome/desktop/input-sources/xkb-options "['grp_led:scroll', 'numpad:microsoft', 'grp:win_space_toggle', 'caps:escape']"
```
