---
layout: post
title: "before_action v.s. before_filter"
date: 2014-12-26 00:11:03 +0800
comments: true
categories: rails
---
To figureout what differece between before_action and before_filter, we should understand what difference between **action** and **filter**.  

1. An action is a method of a controller to which you can route to.  
For example, your user creation page might be routed to UsersController#new - new is the action in this route.

2. Filters run in respect to controller actions - before, after or around them.  
These methods can halt the action processing by redirecting or set up common data to every action in the controller.

3. 
Rails 4 --> *_action  
Rails 3 --> *_filter
