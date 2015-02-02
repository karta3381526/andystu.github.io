---
layout: post
title: "How to install ruby and rails on Windows"
date: 2014-12-18 09:07:30 +0800
comments: true
categories: Ruby on Rails 安裝教學
---
## 在Windows上安裝ruby on rails開發環境

##Easy and the quickest way.
###install RailsInstaller
1. Download it (version 3.0.0 and above are recommend)
from [http://railsinstaller.org](http://railsinstaller.org)
2. install it (just click next and next steps, then done.).

#### about bundle errors (can not fetch gems from rubygems default source): how do we solve it?
- Open and edit Gemfile after rails new app
- Change the => source 'https://rubygems.org' to => source 'http://rubygems.org'
- done.

<!--more-->

##Harder way.
###install RubyInstaller
1. Download the package the version you want from [http://rubyinstaller.org](http://rubyinstaller.org)  
generally, we need to download Rubyinstaller and DevKit both (mind 32 or 64-bit platform).
2. click to install rubyinstaller first and then DevKit.  
(記得勾選 Add Ruby...PATH / Associate .rb ....)
3. Unzip DevKit under C:\
```
C:\> cd C:/DevKit
C:\> ruby dk.rb init
C:\> ruby dk.rb install
C:\> gem install json --platform=ruby 
C:\> gem install bundler
C:\> gem install rails --no-rdoc --no-ri
```
- Done!!