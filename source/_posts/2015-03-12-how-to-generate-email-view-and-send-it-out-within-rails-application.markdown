---
layout: post
title: "how to generate email view and send it out within rails application"
date: 2015-03-12 15:27:14 +0800
comments: true
categories: [rails, actionmailer, view]
---
- If we want to send email within rails app, we could use generator for creating mailer class and view.
``` bash
$ rails g mailer NewsMailer # NewsMailer is the name of mailer class
```

- After that, we could get generated files under app folder.
```
  create  app/mailers/news_mailer.rb
  create  app/mailers/application_mailer.rb
  invoke  erb
  create    app/views/news_mailer
  create    app/views/layouts/mailer.text.erb
  create    app/views/layouts/mailer.html.erb
```

- Next, we need to edit mailer class (news_mailer.rb contains empty mailer so we need to edit it.)
``` ruby
class NewsMailer < ApplicationMailer
  default from: 'news@demo.com'
 
  def news_email(user, news)
    @user = user
    @news = news
    mail(to: @user.email, subject: @news.title)
  end
end
```
<!-- more -->
``` ruby
<!DOCTYPE html>
<html>
  <head>
    <meta content='text/html; charset=UTF-8' http-equiv='Content-Type' />
  </head>
  <body>
    <h1>hi, <%= @user.name %></h1>
    <hr>
    <h2><%= @news.title %></h2>
    <p>
    <%= @news.content.html_safe %>
    </p>
  </body>
</html>
```

- create send_news action in your controller.

``` ruby
#...
def send_news
  @users = User.all
  @news = News.find(1)
  NewsMailer.news_email(@users,@news).deliver
end
#...
```
- Finally, do not forget to add config info to your config/enviroments/$REAIL_ENV.rv file. (here we use gmail)
``` ruby
config.action_mailer.delivery_method = :smtp
config.action_mailer.smtp_settings = {
  address:              'smtp.gmail.com',
  port:                 587,
  domain:               'demo.com',
  user_name:            '<username>',
  password:             '<password>',
  authentication:       'plain',
  enable_starttls_auto: true  }
```

- done.