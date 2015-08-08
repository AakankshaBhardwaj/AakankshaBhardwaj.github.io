---
layout: post
title: "Working with Nokogiri::XML::Node in Rails"
modified:
categories: blog
excerpt:
tags: []
image:
  feature:
date: 2015-08-08T15:39:55-04:00
comments: true
---
I am using gem ```nokogiri``` for ```Nokogiri::XML::Node``` manipulations.here are the some examples
of performing the basics operations on the ```Nokogiri::XML::Node```.you can perform these operations
with ```Nokogiri::XML::Node```.

Say for the example you have the ```Nokogiri::XML::Node``` named ```node```,now here are some basic
operation with this ```node```.

####Get parent:
{% highlight ruby %}
node.parent #=>[10]
{% endhighlight %}
