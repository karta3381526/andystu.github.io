---
layout: post
title: "some link_to usage tips"
date: 2014-12-31 16:57:16 +0800
comments: true
categories: [rails tips, ActionView]
---

### some tips for link_to helper

``` ruby
#in view/xxxx.html.erb

<%= link_to "LINK_NAME", xxx_path %>

<%= link_to "LINK_NAME", "LINK_URL", id: "ID_NAME", class: "CLASS_NAME" %>


# use it like a block
# 1
link_to "LINK_URL" do 
  image_tag "IMAGE_FILE"
end

# 2
link_to xxx_path do 
  image_tag "IMAGE_FILE"
end

```


