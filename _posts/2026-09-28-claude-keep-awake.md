---
title: Claude Keep-Awake
date: 2026-09-28 12:00:00 +0300
categories: [Tools, Python]
tags: [claude, windows, python, vscode]
description: "A small Python script that keeps Windows awake while Claude Code is working in VS Code."
image:
  path: /assets/img/images/claude-keep-awake.webp
  alt: Claude Keep-Awake
---

[Claude Keep-Awake](https://github.com/nisanMan/claude-keep-awake) is a small Python script for Windows that stops the computer from going to sleep while Claude Code is working inside VS Code.
It watches the Claude process tree every few seconds and treats CPU, I/O, or new child processes as activity.
While Claude is active it holds a sleep lock, and after a few quiet minutes, or a 2-hour safety cap, the lock is released.
It is a single file using only the standard library, with no admin rights and no changes to your power settings.
Just clone the repo and run `python keep_awake.py`.
