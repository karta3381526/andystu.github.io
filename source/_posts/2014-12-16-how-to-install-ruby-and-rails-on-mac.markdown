---
layout: post
title: "how to install ruby and rails on Mac"
date: 2014-12-16 17:41:41 +0800
comments: true
categories: Ruby on Rails 安裝教學
---
## 在Mac上安裝ruby on rails開發環境


###1. install rvm
```
#comment
$ \curl -sSL https://get.rvm.io | bash -s stable --ruby  
#(if error message shown -> rvm reinstall 2.1.3 --disable-binary)  
  
#modify .zshrc .bash_profile and relaunch terminal
$ echo progress-bar >> ~/.curlrc  
$ echo "source $HOME/.rvm/scripts/rvm" >> ~/.bash_profile  
$ echo "gem: --no-document" >> ~/.gemrc  
  
#test rvm ready or not  
$ type rvm | head -n 1  
$ rvm list known  
$ rvm install x.x  
$ rvm use 2.1 (rvm use 2.1 --default)
```

###2. install bundler and rails
```
$ gem update --system #更新gem library
$ gem install bundler #安裝bundler
$ gem install rails --no-ri --no-rdoc #安裝rails
```
- Done!!
<!--more-->
