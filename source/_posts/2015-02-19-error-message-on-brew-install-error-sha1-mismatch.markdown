---
layout: post
title: "Error message on brew install: Error: SHA1 mismatch"
date: 2015-02-19 00:46:10 +0800
comments: true
categories: [brew install, error message, solution]
---
- Sometimes we might get error message when we use brew install xxxxx_package.
- What can we do to solve this?
- We could just remove the package which we already download.

- e.g.
```
...
Error: SHA1 mismatch
...
$ rm /Library/Caches/Homebrew/libpng-1.6.16.tar.xz
# and install it again
$ brew install libpng
...
```

- done.