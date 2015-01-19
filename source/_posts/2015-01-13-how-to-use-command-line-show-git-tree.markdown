---
layout: post
title: "how to use command line show git tree"
date: 2015-01-13 18:11:36 +0800
comments: true
categories: git
---
``` bash
$ git log --pretty=oneline --graph --decorate --all
$ git log --oneline --graph --decorate --all
$ gitk --simplify-by-decoration --all
$ gitk --all
$ git show-branch --all
$ git log --all --graph --decorate --oneline --simplify-by-decoration
```