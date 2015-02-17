---
layout: post
title: "heroku command line tips"
date: 2015-02-17 15:44:05 +0800
comments: true
categories: [heroku,command line]
---
```
$ heroku apps:rename NEW_APP_NAME # for rename app
$ heroku create NEW_APP_NAME # for create new name
$ heroku pg:reset DB_NAME # for reset DB
$ git remote add heroku git@heroku.com:project.git
$ heroku git:remote -a APP_NAME
$ heroku keys:add
```