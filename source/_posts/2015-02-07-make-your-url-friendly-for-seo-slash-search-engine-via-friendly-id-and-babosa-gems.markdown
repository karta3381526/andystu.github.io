---
layout: post
title: "make your url friendly for SEO/search engine via friendly id and babosa gems"
date: 2015-02-07 21:07:46 +0800
comments: true
categories: 
---
### If we want add more info with ID in URL for specific instance of model, the easy way is to override the to_param method.
``` ruby
class Model < ActiveRecord::Base

  def to_params
    "#{id} #{title}".parameterize #
  end

end
```
<!-- more -->
- However, we still need the ID at the start of our parameterized URL value for Rails ActiveRecord to find the correct model instance. If we don’t want IDs to be presented in URLs at all, the friendly_id gem is a great choice for this.

- How to install and use [friendly_id](https://github.com/norman/friendly_id) in your rails project. 
- Here we also install [babosa](https://github.com/norman/babosa) for multiple languages.

``` ruby
# add this to your Gemfile
gem 'friendly_id'
gem 'babosa' # this is for locale sensitive transliteration, with support for many languages.
```

``` bash
# in rails project

$ rails generate friendly_id
$ rails generate migration add_slug_to_models slug:string
$ rake db:migrate

#in rails console

If all have been already done, we should run rails console and save all our model records again.
> Model.find_each(&:save)
```
<!-- more -->
### modify our rails model
``` ruby
# edit app/models/model.rb
class Model < ActiveRecord::Base
  extend FriendlyId
  friendly_id :column_name, use: :slugged

  # :history => won't change friendly id after updating :column_name
  # :finder => no need to add .friendly method with Model anymore (gem's version should be above v5.0)
  # use: [:slugged, :history, :finder]


  # for genereate friendly_id
  def should_generate_new_friendly_id?
    new_record? || slug.blank?
  end

  # for locale sensitive transliteration with friendly_id
  def normalize_friendly_id(input)
    input.to_s.to_slug.normalize.to_s
  end

end
```

reference
http://rubysnippets.com/2013/02/04/rails-seo-pretty-urls-in-rails/


