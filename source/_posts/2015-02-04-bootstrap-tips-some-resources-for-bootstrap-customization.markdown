---
layout: post
title: "bootstrap tips: some resources for bootstrap customization"
date: 2015-02-04 10:48:54 +0800
comments: true
categories: [bootstrap, customization]
---
- useful online tools for generating bootstrap theme

http://pikock.github.io/bootstrap-magic/

http://www.lavishbootstrap.com/

http://paintstrap.com/

http://paintstrap.com/gallery/

http://bootswatchr.com/

http://stylebootstrap.info/

http://bootsnipp.com/

<!--more-->
- fake images

http://lorempixel.com

http://placekitten.com

http://placehold.it


- desktop tools

http://www.pingendo.com/

- layout tools

http://www.layoutit.com/

- useful plug-ins

http://vitalets.github.io/x-editable/

https://github.com/rorlab/bootstrap-tagsinput-rails

http://timschlechter.github.io/bootstrap-tagsinput/examples/

- important reference

http://getbootstrap.com/customize/

http://mashable.com/2013/10/20/bootstrap-editors/

https://github.com/twbs/bootstrap-sass/tree/master/assets/stylesheets/bootstrap/mixins

- convert tools

gem 'less2sass'
https://rubygems.org/gems/less2sass

don't forget to add twbs-font-path on top or variable.sass file
```
// When true, asset path helpers are used, otherwise the regular CSS `url()` is used.
// When there no function is defined, `fn('')` is parsed as string that equals the right hand side
// NB: in Sass 3.3 there is a native function: function-exists(twbs-font-path)
$bootstrap-sass-asset-helper: (twbs-font-path("") != unquote('twbs-font-path("")')) !default;
```