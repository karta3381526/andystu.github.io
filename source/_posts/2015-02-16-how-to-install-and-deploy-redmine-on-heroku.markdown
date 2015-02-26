---
layout: post
title: "how to install and deploy redmine 2.6.x on heroku"
date: 2015-02-16 09:40:12 +0800
comments: true
categories: [redmine, heroku, install, deploy]
---

```
$ git clone https://github.com/redmine/redmine.git -b 2.6-stable
$ cd redmine
```
- remove those files from .gitignore
```
Gemfile.lock
Gemfile.local
public/plugin_assets 
config/initializers/session_store.rb 
config/initializers/secret_token.rb 
config/configuration.yml 
config/email.yml
```
<!-- more -->
- remove those block from Gemfile
```
platforms :mri, :mingw do
  # Optional gem for exporting the gantt to a PNG file, not supported with jruby
  group :rmagick do
    # RMagick 2 supports ruby 1.9
    # RMagick 1 would be fine for ruby 1.8 but Bundler does not support
    # different requirements for the same gem on different platforms
    gem "rmagick", (RUBY_VERSION < "1.9" ? "2.13.3" : ">= 2.0.0")
  end

  # Optional Markdown support, not for JRuby
  group :markdown do
    # TODO: upgrade to redcarpet 3.x when ruby1.8 support is dropped
    gem "redcarpet", "~> 2.3.0"
  end
end

platforms :jruby do
  # jruby-openssl is bundled with JRuby 1.7.0
  gem "jruby-openssl" if Object.const_defined?(:JRUBY_VERSION) && JRUBY_VERSION < '1.7.0'
  gem "activerecord-jdbc-adapter", "~> 1.3.2"
end

# and
database_file = File.join(File.dirname(__FILE__), "config/database.yml") if File.exist?(database_file)
  database_config = YAML::load(ERB.new(IO.read(database_file)).result)
    ...
    else
  warn("No adapter found in config/database.yml, please configure it first") end
    else
warn("Please configure your config/database.yml first") end

```

- replace above block with this
```
group :development, :test do
  gem 'sqlite3'
end

group :production do
  gem 'pg'
  gem 'rails_12factor'
  gem 'thin' # change this if you want to use other rack web server
end
```

- bundle it without production
```
$ bundle install --without production test
```
- generate secret token for redmine
```
$ rake generate_secret_token
```
- create heroku app
```
$ heroku create APP_NAME
```

- To avoid aborting when deploying to heroku, we have to do the following two steps: In config/environment.rb we have to remove (or comment) line 10, where it says
```
exit 1
# remove it or comment it
# exit 1
```

- add this under config/application.rb
```
...
module RedmineApp
  classApplication<Rails::Application
    config.assets.initialize_on_precompile = false # add this line
...
```


```
$ git add -A
$ git commit -m "preparing for heroku" 
$ git push heroku 2.6-stable:master
```

```
$ heroku run rake db:migrate
$ heroku run rake redmine:load_default_data
$ heroku open

# Logging into the application
# Use default administrator account to log in:
#
# login: admin
# password: admin
# 
# if you want to reset db, run the following command
# heroku pg:reset DB_NAME
```

- done.