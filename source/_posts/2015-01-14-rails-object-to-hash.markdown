---
layout: post
title: "Rails Object to hash"
date: 2015-01-14 12:26:38 +0800
comments: true
categories: [rails,object,hash]
---

``` ruby
$ rails c
# irb
# Model object -> hash
> @post = Post.first
> @post.attributes

# OpenStruct object -> hash
> @post = OpenStruct.new(title:"this is title", description:"Hello world!")
> @post.to_h
# equals to -> ActionController::Parameters.new(@p.to_h)
```
