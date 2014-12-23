---
layout: post
title: "learning notes for 12in12 week 1"
date: 2014-12-22 17:17:40 +0800
comments: true
categories: 12in12學習筆記
---

### CREATE OUR NEW RAILS APPLICATION
```
$ rails new reddit
$ cd reddit
$ git init
$ git add .
$ git commit -m "reddit init"
```
### LINK SUBMISSIONS
```
$ git checkout -b link_scaffold
$ rails g scaffold link title:string url:string
$ rake db:migrate
$ git add .
$ git commit -m "Generate Links Scafffold"
$ git checkout master
$ git merge link_scaffold
```

```
$ git checkout -b add_users
$ bundle install # after add devise into Gemfile
$ rails g devise:install 
```

- then modify config/env.../deve... for mail
- add flash in app/views/layouts/application.html.erb

``` ruby app/views/layouts/application.html.erb
<% flash.each do |name, msg| %>
  <%= content_tag :div, msg, class: "alert alert-#{name}" %>
<% end %>
```

### USERS
``` bash add devise gem
$ rails g devise:views
$ rails g devise User
$ rake db:migrate
```
```
$ git status
$ git add .
$ git commit -am "Add devise and create User model"
```
``` ruby app/views/links/index.html.erb
<% if user_signed_in? %>
  <ul>
    <li><%= link_to 'Submit link', new_link_path %></li>
    <li><%= link_to 'Account', edit_user_registration_path %></li>
    <li><%= link_to 'Sign out', destroy_user_session_path, :method => :delete %></li>
  </ul>
<% else %>
  <ul>
    <li><%= link_to 'Sign up', new_user_registration_path %></li>
    <li><%= link_to 'Sign in', new_user_session_path %></li>
  </ul>
<% end %>
```
``` ruby app/models
# app/models/user.rb
has_many :links
  
# app/models/link.rb
belongs_to :user
```
```
$ rails g migration add_user_id_to_links user_id:integer:index
$ rake db:migrate
```
```
$ git status
$ git add .
$ git commit -am "Add association between Link and User"
```
``` ruby app/controllers/links_controller.rb
before_filter :authenticate_user!, :except => [:index, :show]
...
def new
@link = current_user.links.build
end

def create
@link = current_user.build(link_params)
...
end
```

``` ruby app/views/links/index.html.erb
<% if link.user == current_user %>
  <td><%= link_to 'Edit', edit_link_path(link) %></td>
  <td><%= link_to 'Destroy', link, method: :delete, data: { confirm: 'Are you sure?' } %></td>
<% end %>
```

``` ruby app/controllers/links_controller.rb
...
before_action :authorized_user, only: [:edit, :update, :destroy]
...
private
...

def authorized_user
  @link = current_user.links.find_by(id: params[:id])
  redirect_to links_path, notice: "Not authorized to edit this link" if @link.nil?
end
```

```
$ git status
$ git commit -am "Authorization on links"
$ git checkout master
$ git merge add_users
```
### STRUCTURE AND SOME STYLING
