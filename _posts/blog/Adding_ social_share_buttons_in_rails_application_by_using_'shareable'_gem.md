---
layout: post
title: "Creating a circular progress Bar by using SVG path"
modified:
categories: blog
excerpt:
tags: []
image:
  feature:
date: 2015-05-26T15:39:55-04:00
comments: true
---
However in practice you need to add social sharing buttons inside your rails applications. Its very easy to add social buttons in rails application by using 'shareable' gem.

here is an example:

### Install Gem

put gem  'shareable' in your gem file.
then run 
{% highlight ruby %}
bundle install.
{% endhighlight %}

### Show buttons in rails view:

put {% highlight ruby %} <%= render_shareable %> {% endhighlight %} in your view
this will add default buttons in your view.

### Customizing buttons:

you can customize buttons by using the helper methods.
for more detail click [here](https://github.com/hermango/shareable).

