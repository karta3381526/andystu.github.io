---
layout: post
title: "install Lavish on Ubuntu 14.04"
date: 2015-03-20 09:21:56 +0800
comments: true
categories: [lavish, bootstrap, ubuntu]
---
- Lavish is a Bootstrap theme generator by Quan. It can generate both CSS and LESS code from an image you provide. Then, you can customize it.

- Recently, I want to install on my ubuntu server for using it locally and conviniently.

- the following steps are my install howto:

```
$ git clone https://github.com/mquan/lavish.git
$ cd lavish/
$ rvm install 1.9.3
$ rvm use 1.9.3
$ bundle install --without production

$ sudo apt-get install libmagickwand-dev # for solving rmagick install problem

$ sudo add-apt-repository ppa:chris-lea/node.js # optional
$ sudo apt-get -y update # optional

$ sudo apt-get -y install nodejs # for ExtJS

$ rails s # open http://localhost:3000/ and enjoy it.
```

- done.

