---
published: true
title: Shortcuts
layout: post
tags: [sublime,text,ide]
categories: [ide,sublime-text]
permalink: /2014/02/shortcuts/
---

```
[
{ "keys": ["alt+m"], "command": "markdown_preview", "args": {"target": "browser"} },
    { "keys": ["alt+a"], "command": "toggle_side_bar" },
    { "keys": ["alt+s"], "command": "focus_side_bar" },
    { "keys": ["alt+d"], "command" : "toggle_minimap"},
    { "keys": ["alt+z"], "command": "toggle_bookmark" },
    { "keys": ["ctrl+shift+d"], "command": "find_under_expand" },
    { "keys": ["ctrl+d"], "command": "duplicate_line" },
    { "keys": ["alt+f"], "command": "goto_definition" },
    { "keys": ["alt+shift+7"],
        "caption": "2 cols (full - 2)",
        "command": "set_layout",
        "args":
        {
            "cols": [0.0, 0.5, 1.0],
            "rows": [0.0, 0.5, 1.0],
            "cells": [ [0, 0, 1, 2], [1, 0, 2, 1], [1, 1, 2, 2] ]
        }
    }
]
```
