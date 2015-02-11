---
layout: post
title: "how to fix simple search of octopress"
date: 2015-02-11 14:37:17 +0800
comments: true
categories: [octopress, google site search, simple search, fix]
---

### find navigation.html in /source/_includes and replace original code with new code
``` html
...
<form action="{{ site.simple_search }}" method="get">
  <fieldset role="search">
<!-- original code  -->
<!--     <input type="hidden" name="q" value="site:{{ site.url | shorthand_url }}" /> -->
<!-- //original code  -->

<!-- new code -->
    <input type="hidden" name="sitesearch" value="{{ site.url | shorthand_url }}" />
<!-- //new code -->
    <input class="search" type="text" name="q" results="0" placeholder="Search"/>
  </fieldset>
</form>
...
```

done.

reference
http://kaspars.net/blog/wordpress/how-to-add-google-site-search