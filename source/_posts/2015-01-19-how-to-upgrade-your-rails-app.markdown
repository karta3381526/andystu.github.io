---
layout: post
title: "how to upgrade your rails app?"
date: 2015-01-19 10:50:23 +0800
comments: true
categories: 
---

- updating the Rails version in the Gemfile and run this rake task.
```
# Gemfile
# Bundle edge Rails instead: gem 'rails', github: 'rails/rails'
gem 'rails', '4.x.x' # <- updating the version of rails info

$ rake rails:update
```
#### done.

http://edgeguides.rubyonrails.org/upgrading_ruby_on_rails.html