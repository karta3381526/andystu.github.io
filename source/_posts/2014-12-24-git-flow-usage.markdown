---
layout: post
title: "git flow usage"
date: 2014-12-24 23:34:12 +0800
comments: true
categories: git
---
### git-flow usage notes
- install git-flow on Mac
``` bash
$ brew install git-flow # Done
```

- usage how-to (for feature)

``` bash
$ git flow init # under project folder, git-flow would ask few questions, using the default value is recommended. 
$ git flow feature start MY_FEATURE # XXX is branch name
# add some files or do something ...
$ git add .
$ git commmit -am 'do something ...'
$ git flow feature publish MY_FEATURE # push to remote repo
$ git flow feature finish MY_FEATURE
```

- usage how-to 2 (for release)

``` bash
$ git flow release start RELEASE [BASE] 
# e.g. git flow release start Version_1.0
$ git add .
$ git commit -am 'do something ...'
$ git flow release finish RELEASE
```

#### [recommand reference]
http://danielkummer.github.io/git-flow-cheatsheet/   
http://fireqqtw.logdown.com/posts/206951-git-flow-notes

