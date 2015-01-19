---
layout: post
title: "how to make jquery event work in rails app?"
date: 2015-01-19 11:08:28 +0800
comments: true
categories: 
---

- To make jquery event work, the easiest way is to use jquery.turbolinks.

- To install it, just add this to your Gemfile:

```
gem 'jquery-turbolinks'

# and add this to your assets/javascripts/application.js file.

//= require jquery.turbolinks

# and it should be worked good.
```

#### done.

http://stackoverflow.com/questions/17881384/jquery-gets-loaded-only-on-page-refresh-in-rails-4-application