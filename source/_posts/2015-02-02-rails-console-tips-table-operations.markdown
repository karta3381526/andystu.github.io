---
layout: post
title: "rails console tips: table operations"
date: 2015-02-02 18:04:19 +0800
comments: true
categories: [rails console, rails tips, ActiveRecord]
---
##In rails console, you can

### list tables
``` ruby
> ActiveRecord::Base.connection.tables
```
### list a table structure (but it is a protected method)
``` ruby
# this dose not work. 
> ActiveRecord::Base.connection.table_structure("projects")

# we should utilize send method to call protected method
> @c = ActiveRecord::Base.connection
> @c.send(:table_structure, "xxxs") # xxxs is your model name
```