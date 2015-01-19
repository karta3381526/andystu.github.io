---
layout: post
title: "change default web server and timezone for heroku"
date: 2015-01-09 12:17:25 +0800
comments: true
categories: [heroku, web server, timezone]
---
- add web server gem to your Gemfile
``` ruby
group :production do
  gem 'pg'
  gem 'rails_12factor'
  gem 'thin' # web server : thin
end
```
- bundle it for updating your Gemfile.lock
``` bash
$ bundle install
$ git add .
$ git commit -am 'bundle and update Gemfile.lock'
```
- deploy to heroku
```
$ git push heroku master
```
#### done.

- time zone config for heroku
``` bash
$ heroku config:add TZ=Asia/Taipei
```
#### done.

- for reset pg DB
```
$ heroku pg:reset DATABASE_URL --confirm heroku_app_name
```

