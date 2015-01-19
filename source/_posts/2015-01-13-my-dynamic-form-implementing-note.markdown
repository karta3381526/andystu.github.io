---
layout: post
title: "dynamic form implementing note"
date: 2015-01-13 14:40:41 +0800
comments: true
categories: [dynamic form, rails tips]
---

```
$ rails g scaffold product name price:decimal
$ rails g scaffold product_type name
$ rails g scaffold product_field name field_type required:boolean product_type:belongs_to
$ rails g migration add_type_to_product product_type:belongs_to properties:text
$ rake db:migrate
```

``` ruby 
# config/routes.rb
...
  resources :product_types

  resources :products
  root 'products#index'
...
```
<!--more-->

``` js
# assets/javascripts/product_types.js.coffee

$(document).on 'click', 'form .remove_fields', (event) ->
  $(this).prev('input[type=hidden]').val('1')
  $(this).closest('fieldset').hide()
  event.preventDefault()

$(document).on 'click', 'form .add_fields', (event) ->
  time = new Date().getTime()
  regexp = new RegExp($(this).data('id'), 'g')
  $(this).before($(this).data('fields').replace(regexp, time))
  event.preventDefault()
```

``` ruby
# models/product.rb
class Product < ActiveRecord::Base
  belongs_to :product_type
  serialize :properties, Hash

  def validate_properties
    product_type.product_fields.each do |field|
      if field.required? && properties[field.name].blank?
        errors.add field.name, "must not be blank"
      end
    end
  end
  
end

# models/product_type.rb
class ProductType < ActiveRecord::Base
  has_many :fields, class_name: 'ProductField'
  accepts_nested_attributes_for :fields, allow_destroy: true
#  has_many :product_fields
#  accepts_nested_attributes_for :product_fields, allow_destroy: true
end

# models/product_field.rb
class ProductField < ActiveRecord::Base
  belongs_to :product_type
end

```

``` ruby
# product_types_controller.rb 
# product_types_params should be modified for its nested attributes
def product_type_params
  params.require(:product_type).permit(:name, fields_attributes: [:name, :field_type, :required, :product_type_id])
end

# products_controller.rb 
# product_params need to be modified for its column properties
def product_params
  # all_properties = params.require(:product).fetch(:properties)
  # params.require(:product).permit(:name, :price, :product_type_id, :properties).merge(:properties => all_properties)
  params.require(:product).permit!
end

# products_controller.rb 
# for generating dynamic form, action new also need to pass its product_type_id to view.
  def new
    @product = Product.new(product_type_id: params[:product_type_id])
  end
```

``` ruby
# application_helper.rb

module ApplicationHelper
  def link_to_add_fields(name, f, association)
    new_object = f.object.send(association).klass.new
    id = new_object.object_id
    fields = f.fields_for(association, new_object, child_index: id) do |builder|
      render(association.to_s.singularize + "_fields", f: builder)
    end
    link_to(name, '#', class: "add_fields", data: {id: id, fields: fields.gsub("\n", "")})
  end
end
```

``` ruby
# product_types/_form.html.erb
<%= form_for(@product_type) do |f| %>
  ...
  <div class="field">
    <%= f.label :name %><br>
    <%= f.text_field :name %>
  </div>

  <%= f.fields_for :fields do |builder| %>
    <%= render "field_fields", f: builder %>
  <% end %>
  <%= link_to_add_fields "Add Field", f, :fields %>

  <div class="actions">
    <%= f.submit %>
  </div>
<% end %>

# add product_types/_product_field_fields.html.erb
<fieldset>
  <%= f.select :field_type, %w[text_field check_box shirt_sizes] %>
  <%= f.text_field :name, placeholder: "field_name" %>
  <%= f.check_box :required %> <%= f.label :required %>
  <%= f.hidden_field :_destroy %>
  <%= link_to "remove", '#', class: "remove_fields" %>
</fieldset>

# product_types/show.html.erb
<p id="notice"><%= notice %></p>
<p>
  <strong>Name:</strong>
  <%= @product_type.name %>
</p>
<p>
  <strong>Fields:</strong>
  <%= @product_type.fields.each do |f| %>
  <br>
  <%= f.name %>
  <br>
  <%= f.field_type %>
  <% end -%>
</p>
...

# products/_form.html.erb
...
  <div class="field">
    <%= f.label :price %><br>
    <%= f.text_field :price %>
  </div>

  <%= f.fields_for :properties, OpenStruct.new(@product.properties) do |builder| %>
    <% @product.product_type.fields.each do |field| %>
      <%= render "products/fields/#{field.field_type}", field: field, f: builder %>
    <% end %>
  <% end %>

  <div class="actions">
    <%= f.submit %>
  </div>
<% end %>

# products/index.html.erb
...
<%= form_tag new_product_path, method: :get do %>
  <%= select_tag :product_type_id, options_from_collection_for_select(ProductType.all, :id, :name) %>
  <%= submit_tag "New Product", name: nil %>
<% end %>

```
### tips: OpenStruct.new(@product.properties) 

*Without OpenStruct.new object, we can't edit and update hash properties data of the record.*

#### done.