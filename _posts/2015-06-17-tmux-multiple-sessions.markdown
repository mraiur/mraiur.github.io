---
published: true
title: Run multiple scripts in tmux session
layout: post
tags: [ubuntu,tmux]
categories: [ubuntu,tools]
permalink: 2015/06/run-multiple-scripts-in-tmux-session/
---
Most of my development i need to have a gulp/grunt script that will manage my resources( css, sass, js etc ). Some times i need a livereload server ( livereloadx ) and from some time i need a node server running.

It kinda annoying to run all the scripts every day. You can setup a bash script to do that for you.

If you want a windowed version like this:

[![](/files/tmux/tmux-windowed-300x188.jpg)](/files/tmux/tmux-windowed.jpg)

The script looks like this:

```
tmux new-session -s development -n editor -d
tmux send-keys -t development:1 'cd ~/work/SCRIPT_1.sh' C-m

tmux new-window -n resources -t development
tmux send-keys -t development:2 'cd ~/work/SCRIPT_2.sh' C-m

tmux new-window -n livereload -t development
tmux send-keys -t development:3 'cd ~/work/SCRIPT_3.sh' C-m

tmux select-window -t development:0

tmux attach -t development
```

This will create a session named "development" and create three windows and execute a script in each window.

But if you prefer to run several scripts in single window, but in different pane's:

[![](/files/tmux/tmux-single-window-300x188.jpg)](/files/tmux/tmux-single-window.jpg)

The script looks like this:

```
tmux new-session -s development -n editor -d
tmux send-keys -t development:1 'cd ~/work/SCRIPT_1.sh' C-m

tmux split-window -v -t development
tmux select-layout -t development main-horizontal

tmux split-window -v -t development
tmux select-layout -t development main-vertical

tmux send-keys -t development:1.1 'cd ~/' C-m
tmux send-keys -t development:1.2 'cd ~/work/SCRIPT_2.sh' C-m
tmux send-keys -t development:1.3 'cd ~/work/SCRIPT_3.sh' C-m

tmux select-window -t development:0

tmux attach -t development
```
