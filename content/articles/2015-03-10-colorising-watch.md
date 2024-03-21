---
title: Colourising Watch
layout: post
published_date: 2015-03-10 11:30:00 +0100
categories:
  - coding
---

For many years I had assumed (based on some comments in forums) that the `watch` unix command had a bug, and could not display colourised terminal output, even when using the `-c` colour option.

This made me sad.

Recently I've been writing tests in py.test, which colourises the output in red for failed test cases. My tests take less than 1s, so while I'm writing them, I run `watch py.test`, watch it fail, and keep writing it till it passes. 

After a few days of non-coloured output, I resumed my search and found [this](http://stackoverflow.com/questions/10776977/more-command-alternative-that-does-support-colors). My search was over!

The simple solution is this: Not only must watch be told (with `-c`) to interpret colours, but the command you are watching must be too. This is because both operate in `color=auto` mode; colours are only output if the program detects it is being run in an interactive terminal, not a pipe.

I simply ran `watch -c py.test --color=yes` and shed tears of joy!
