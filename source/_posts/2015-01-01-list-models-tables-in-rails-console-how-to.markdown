---
layout: post
title: "rails tips: list models (tables) (how-to)"
date: 2015-01-01 10:26:13 +0800
comments: true
categories: [rails tips, ActiveRecord]
---

``` ruby
$ rails c
 ActiveRecord::Base.connection.tables.each do |table_name|
  puts "\n" + table_name
  ActiveRecord::Base.connection.columns(table_name).each {|c| puts "- " + c.name + ": " + c.type.to_s + " " + c.limit.to_s}
 end

# or
 Model.column_names
 
# or
 Model
```

``` ruby
> ActiveRecord::Base.connection.tables # list all models retuen as an array
> ActiveRecord::Base.connection.columns(table_name) # list model(table) detail
``` 


