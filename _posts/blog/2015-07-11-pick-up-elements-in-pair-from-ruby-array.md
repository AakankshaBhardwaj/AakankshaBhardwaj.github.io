---
layout: post
title: "Pick up elements in pair from ruby array"
modified:
categories: blog
excerpt:
tags: []
image:
  feature:
date: 2015-07-11T15:39:55-04:00
comments: true
---

Hi Friends,

However in practice we often require to select elements of the array in pairs. It's very easy to do it with ruby array.
Here is an example for the same:
 
### Example
{% highlight ruby %}
arr = [1,2,3,4,5,6,7,8,9,10]

To pick elements of ```arr``` in the pair of ```3```, Here we go
arr.each_slice(3) do |pair|
puts pair
end

#=>[1, 2, 3]
#=>[4, 5, 6]
#=>[7, 8, 9]
#=>[10]
{% endhighlight %}

```each_slice``` method slice the original array in the given number of size.If you want to pick ```5``` elements of 
the array then just modify above example by this:

{% highlight ruby %}
 arr.each_slice(5) do |pair|
 puts pair
 end
 
#=>[1, 2, 3,4,5]
#=>[6, 7, 8,9,10]
{% endhighlight %}
