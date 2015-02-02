---
layout: post
title: "rails app deploy to heroku : an easy way"
date: 2015-01-06 23:24:04 +0800
comments: true
categories: [rails tips, heroku, deploy]
---

### Preparing step
- install Postgres DB via brew
``` bash
$ brew doctor
$ brew update
$ brew install postgresql

# if we want to run pg locally, we need to run the following instructions.

# To have launchd start postgresql at login:
ln -sfv /usr/local/opt/postgresql/*plist ~/Library/LaunchAgents

# Then to load and run postgresql immediately:
launchctl load ~/Library/LaunchAgents/homebrew.mxcl.postgresql.plist
```
- download and install heroku toolkit  
https://toolbelt.heroku.com/
- initialization of heroku under your rails project
``` bash
$ heroku login
$ heroku create
```
- Open the file called Gemfile in your text editor and find the line containing:
``` ruby
gem 'sqlite3'
```
- Remove that line and replace it with:

``` ruby
group :development, :test do
  gem 'sqlite3'
end

group :production do
  gem 'pg'
  gem 'rails_12factor'
end
```
- bundle install
``` ruby
$ bundle install --without production
```
- git add . and git commit
``` bash
$ git add .
$ git commit -m "Changed Gemfile for heroku"
```
- finally, push to heroku
``` bash
$ git push heroku master
$ heroku run rake db:migrate
```