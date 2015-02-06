---
layout: post
title: "ujs / sjr usage hint"
date: 2015-02-05 10:52:25 +0800
comments: true
categories: 
---
### ujs / sjr usage hint for rails link_to method and form! 
```
A. Enable feature of ajax for Link
  1. link_to 要加 remote: true, path 要是 .js 的 format
  2. 要確保後端 action 支援 .js format
  3. 必須要有 #{action}.js.erb

B. Enable feature of ajax for Form
  1. form_for(@record, format: :js, remote: true)
  2. 確保後端 action 支援 .js format
  3. 必須要有 #{action}.js.erb

對應的 js.erb 必須處接下來的事情 e.g. 刪除資料、redirects、update forms ... etc
```