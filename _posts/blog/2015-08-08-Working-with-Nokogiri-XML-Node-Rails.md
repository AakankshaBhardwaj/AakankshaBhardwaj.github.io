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

####1. Get parent:
{% highlight ruby %}
node.parent #=> will return of the xpath of the node in document.
{% endhighlight %}

####2. Get xpath:
{% highlight ruby %}
node.path #=>will return of the xpath of the node in document
{% endhighlight %}

####3. Get node at some path in document:
{% highlight ruby %}
_node = doc.xpath('some_path')
 #=>where doc is a nokogiri document.it will return a nodeset if you want to get the exact node then do this.
 _node = doc.xpath('some_path')[0] or _node = doc.xpath('some_path').first
{% endhighlight %}

####4. Get children:
{% highlight ruby %}
node.children
 #=>will return the ```nodeset``` of childs of node your can select them according to your need.
{% endhighlight %}

####5. Add children:
{% highlight ruby %}
node.add_child('child_html')
 #=> add child in as the last child.
{% endhighlight %}

####6. Add siblings:
{% highlight ruby %}
node.add_next_sibling('some_html') #=>  add a sibling node after the node in parent.
node.add_previous_sibling('some_html') #=>  add a sibling node before the node in parent node.
{% endhighlight %}

####7. Replace a node:
{% highlight ruby %}
node.replace('replace_node's_html') #=> replace a node by given html.
{% endhighlight %}

####8. Styling a node:
{% highlight ruby %}
node['class'] = 'some_css_class' #=>  add a css class to node.
css_class = node['class']  #=>  get the css_class of the node.
{% endhighlight %}

####9. Show html:
{% highlight ruby %}
node.to_html  #=>  will return html of the node.
{% endhighlight %}

