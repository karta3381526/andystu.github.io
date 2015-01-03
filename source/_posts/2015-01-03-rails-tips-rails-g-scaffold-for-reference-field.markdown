---
layout: post
title: "rails tips: rails g scaffold for reference field"
date: 2015-01-03 11:02:27 +0800
comments: true
categories: [rails tips, scaffold]
---

Rails scaffold generators are very smart! you can use belongs_to to quickly add relations. 
In the following example, I have 2 models products and product_types; 
Product_types belong to product and product has many product types.

``` bash
$ rails g scaffold product name:string
$ rails g scaffold product_type name:string product:belongs_to

# You can also use :references
$ rails g scaffold product_type name:string product:references

# For more manually work, you can do it like this
$ rails g scaffold product_type name:string product_id:integer
# then add "belongs_to" in your ProductType model
```
This will generate the necessary columns, indexes and associations in your models.