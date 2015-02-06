---
layout: post
title: "How to fix Octopress build warning Layout nil requested after installing some themes"
date: 2015-02-06 14:17:39 +0800
comments: true
categories: 
---
#### How to fix Octopress "build warning Layout nil requested"
``
After changing some themes of octopress then rake generate might produce some errors like this:
Build Warning: Layout 'nil' requested in .....atom.xml does not exist.
``

#### Fix by replacing:

`layout: nil`
with:
`layout: null`
in files:
``
source/atom.xml
source/robots.txt
source/_includes/custom/category_feed.xml
``