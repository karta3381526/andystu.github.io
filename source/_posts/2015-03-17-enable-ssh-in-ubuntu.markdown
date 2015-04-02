---
layout: post
title: "enable ssh in ubuntu"
date: 2015-03-17 00:50:27 +0800
comments: true
categories: [ubuntu, ssh]
---
- for ubuntu 14.04, we need to install OpenSSH Server

```
$ sudo apt-get install openssh-server
```

- next, we might want to configure your ssh service

```
# edit sshd config file
$ sudo nano /etc/ssh/sshd_config
```

- finally, restart it.
```
$ sudo /etc/init.d/ssh restart
```

- done.