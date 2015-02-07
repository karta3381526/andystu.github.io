---
layout: post
title: "how to get a list of a class or instance methods by keyword"
date: 2015-02-06 23:29:43 +0800
comments: true
categories: 
---

#### a very useful tip to find methods in ruby/rails console

``` ruby
# Class.methods.grep(/keyword/) 

# e.g. 
irb> 1.methods.grep(/to/) #  => [:to_s, :to_f, :to_default_s, :to_json, :upto, :downto, :to_i, :to_int, :numerator, :denominator, :to_r, :to_bn, :to_d, :singleton_method_added, :to_c, :to_formatted_s, :to_param, :to_query, :psych_to_yaml, :to_yaml, :to_yaml_properties, :singleton_class, :singleton_methods, :respond_to?, :singleton_method, :define_singleton_method, :to_enum]

# Class.instance_methods.grep(/method/) #  => [:instance_methods, :public_instance_methods, :protected_instance_methods, :private_instance_methods, :methods, :singleton_methods, :protected_methods, :private_methods, :public_methods]

# Class.methods.grep(/new/) # => ["new"]
```