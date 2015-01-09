---
layout: post
title: "rails tips: user authentication using devise"
date: 2015-01-08 11:04:33 +0800
comments: true
categories: [devise, rails tips, gem]
---
- create a demo project by rails
``` ruby
$ rails new topic
```
- add gem 'devise' to Gemfile then bundle it.
``` ruby
# Gemfile
gem 'devise'

$ bundle
```
- install into your project, generate user model and views
``` ruby
$ rails generate devise:install
$ rails generate devise User
$ rails generate devise:views
```
- configure development.rb for action mailer setting
``` ruby
config.action_mailer.default_url_options = { host: 'localhost', port: 3000 }
config.action_mailer.delivery_method = :smtp
```
- configure application.rb for action mailer setting
``` ruby
ActionMailer::Base.smtp_settings = {
 
        :address        => 'smtp.gmail.com',
        :domain         => 'mail.google.com',
        :port           => 587,
        :user_name      => "your_gmail_account@gmail.com", #ENV['GMAIL_USERNAME'],
        :password       => "weakpass", #ENV['GMAIL_PASSWORD'],
        :authentication => 'login',
        :enable_starttls_auto => true
}
```
- generate a scaffold for the topic resource and add registrations controller for overriding devise's one
``` ruby
$ rails g scaffold topic title
$ rails g controller registrations 

# in registrations_controller.rb

class RegistrationsController < Devise::RegistrationsController
 
  private
 
  def sign_up_params
    params.require(:user).permit(:name, :email, :password, :password_confirmation)
  end
 
  def account_update_params
    params.require(:user).permit(:name, :email, :password, :password_confirmation, :current_password)
  end 
end

# modify route.rb
devise_for :users, controllers: { registrations: "registrations" }
root 'topics#index'

# add the following "before_action" to topics_conftroller.rb for forcing users logging in
before_action :authenticate_user!

```

##### done and enjoy it.



