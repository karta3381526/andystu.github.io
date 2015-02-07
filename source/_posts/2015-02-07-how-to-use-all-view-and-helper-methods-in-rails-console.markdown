---
layout: post
title: "how to use all view and helper methods in rails console"
date: 2015-02-07 00:56:39 +0800
comments: true
categories: 
---
### run and preview a view helper

``` ruby 
> YourController.helpers.my_helper

> ApplicationController.helpers.content_tag(:div, "Hello World!")
```

### create params in rails console
```
# ActionController::Parameters.new
params = ActionController::Parameters.new({
  person: {
    name: 'Francesco',
    age:  22,
    role: 'admin'
  }
})

```

- reference
http://edgeapi.rubyonrails.org/classes/ActionController/Parameters.html
