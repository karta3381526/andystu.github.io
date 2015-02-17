---
layout: post
title: "rails tip: How to update attributes without save"
date: 2015-02-17 15:31:32 +0800
comments: true
categories: [rails, active record, update attributes]
---
- generally, when we use update_attributes, it will save automatically. however, what if we just want to new an record and update some attributes of it. what can we do?

- We can use *assign_attributes* method.
```
user = User.new
user.assign_attributes({ :name => 'Andy'})
user.name        # => "Andy"
user.new_record? # => true
```