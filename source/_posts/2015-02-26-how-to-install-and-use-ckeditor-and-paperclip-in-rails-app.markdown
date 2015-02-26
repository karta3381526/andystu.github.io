---
layout: post
title: "How to install and use ckeditor and paperclip in rails app"
date: 2015-02-26 14:59:33 +0800
comments: true
categories: [ckeditor, paperclip, install]
---
- In [paperclip](https://github.com/thoughtbot/paperclip) requirement, Paperclip must have access to ImageMagick that must be installed. For Mac OS X, we could run this command with Homebrew.
```
$ brew install imagemagick
```

- add this to your rails app Gemfile.
```
gem 'paperclip'
gem 'ckeditor'
```
- then bundle it.
```
$ bundle
```
- next, we should generate model for [paperclip](https://github.com/galetahub/ckeditor) to store uplaoded files

```
$ rails generate ckeditor:install --orm=active_record --backend=paperclip
```

<!-- more -->

- Don't forget to rake db:migrate

```
$ rake db:migrate
```

- Now, we need to mount it by editing your config/routes.rb

``` ruby
#...
mount Ckeditor::Engine => "/ckeditor"
#...
```

- Add this in your app/assets/javascripts/application.js and make ckeditor working.

```
//= require ckeditor/init
```
- In your form view, change f.text_area to f.cktext_area

``` ruby
<%= form_for @post do |f| -%>
#  ...
  <%= f.cktext_area :content, :class => "form-control" %>
#  ...
<% end -%>
```

- done.