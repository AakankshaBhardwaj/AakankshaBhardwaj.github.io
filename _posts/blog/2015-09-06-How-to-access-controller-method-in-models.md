---
layout: post
title: "How access controller method in models"
modified:
categories: blog
excerpt:
tags: []
image:
  feature:
date: 2015-09-06T15:39:55-04:00
comments: true
---
How ever in practice some time we require to access the controller's methods in the models.It's quite easy to do so in
rails. Here is an explanation of that:

###Add a before_filter method inside the Application Controller
Add a before_filter method inside the application controller and write the following command code inside that function
{% highlight ruby %}
Thread.current.thread_variable_set('controller', self)
{% endhighlight %}

###Access inside the model
Now you can access the controller's method inside the model by using
{% highlight ruby %}
Thread.current.thread_variable_get('controller').method_name
{% endhighlight %}

####Note
You have to make your ```method_name``` public to avoid it calling from browser as action have to hide it by
{% highlight ruby %}
hide_action :method_name
{% endhighlight %}





