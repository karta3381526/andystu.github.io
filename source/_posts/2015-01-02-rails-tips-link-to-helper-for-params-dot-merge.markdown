---
layout: post
title: "rails tips: link_to helper for params.merge"
date: 2015-01-02 16:52:02 +0800
comments: true
categories: [rails tips,link_to,url_for,ActionView]
---
### 
- To preserve the params of url I did this:
``` ruby app/views/index.html.erb
...

<%= link_to 'Foot type', url_for(params.merge(foot_type_id: value)) %>
...

```

``` ruby app/controllers/recipes_controller.rb
...
  def index
    @recipes = Recipe.where(nil)
    @recipes = @recipes.food_type_of(params[:food_type_id]) if (params[:food_type_id])
    @recipes = @recipes.food_preference_of(params[:food_preference_id]) if (params[:food_preference_id])
    @recipes = @recipes.cuisine_of(params[:cuisine_id]) if (params[:cuisine_id])
  end
...
```

### alternative solutions
http://filterrific.clearcove.ca   
http://www.lauradhamilton.com/how-to-filter-by-multiple-options-filterrific-rails   
https://github.com/plataformatec/has_scope   


####[reference]
http://apidock.com/rails/v3.2.13/ActionView/Helpers/UrlHelper/url_for  
http://stackoverflow.com/questions/6625293/how-to-add-parameters-to-current-url-in-rails   
http://www.justinweiss.com/blog/2014/02/17/search-and-filter-rails-models-without-bloating-your-controller/   
http://guides.rubyonrails.org/active_record_querying.html#scopes    