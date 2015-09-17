---
layout: post
title: "How to deploy on heroku"
modified:
categories: blog
excerpt:
tags: []
image:
  feature:
date: 2015-08-22T15:39:55-04:00
comments: true
---

####To deploy rails application on heroku all you need to do is follow these steps:

1)First and the foremost is creating an account on Heroku.

2)Then follow the email sent from heroku.

3)Select your language.

4)Select your Heroku Toolbelt to download.

5)Go to command Prompt 
{% highlight ruby %}
a)$heroku login
Enter your Heroku credentials.
Email: ruby@example.com
Password:
Authentication successful.
{% endhighlight %}

{% highlight ruby %}
b)$heroku create app_name
{% endhighlight %}

{% highlight ruby %}
c)git push heroku master
{% endhighlight %}

Thanks for reading this. 
