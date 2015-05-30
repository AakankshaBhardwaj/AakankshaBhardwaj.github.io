---
layout: post
title: "Design Patterns in Ruby: Singleton"
modified:
categories: blog
excerpt:
tags: []
image:
  feature:
date: 2015-05-30T15:39:55-04:00
comments: true
---
The concept of the Singleton pattern is fairly straightforward: only a single instance of a class can exist.
This can be useful when an application allows only one object to be instantiated for a given class.

Even though there are mixed feelings amongst developers about this pattern, it is often used in other languages, such as Java and C-based languages.
In Ruby, the Singleton module in the standard library can be used to implement this pattern.

### When to use Singleton?
Let’s say that we need to design a class to hold configuration data for our application, and there can only ever exist one instance of this configuration.
Sure, we could simulate a Singleton by creating a module, but we would have to make sure that it could not be duplicated or cloned, otherwise it would lose its purpose.

### Integration
The first step in creating a Singleton class is to <code>require</code> and <code>include</code> the Singleton module in a class:
{% highlight ruby %}
require 'singleton'
 
class SomeClassName
  include Singleton
end
{% endhighlight %}

If you try to instantiate this class as you normally would a regular class, a <code>NoMethodError</code> exception is raised.
The constructor is made private to prevent other instances from being accidentally created:

{% highlight ruby %}
SomeClassName.new

```NoMethodError: private method 'new' called for AppConfig:Class

{% endhighlight %}

