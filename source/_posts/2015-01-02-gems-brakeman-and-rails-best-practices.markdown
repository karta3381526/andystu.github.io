---
layout: post
title: "RubyGems: brakeman and rails_best_practices"
date: 2015-01-02 10:04:02 +0800
comments: true
categories: [rails tips, brakeman, rails_best_practices, rubygems]
---
### brakeman : Ruby on Rails 專案安全性檢測工具
`Brakeman is an open source vulnerability scanner specifically designed for Ruby on Rails applications. It statically analyzes Rails application code to find security issues at any stage of development.`

### rails_best_practices : Ruby on Rails 專案程式碼品質評測工具
`rails_best_practices is a code metric tool to check the quality of rails codes.`
### installation
```
group :development do
  gem "brakeman", require: false  
  gem "rails_best_practices", require: false
end

# require: false => means that we don't want to run that gem when start rails server
```

### usage (recommand using those tools before each commit)
```
$ brakeman  

$ rails_best_practices  
```