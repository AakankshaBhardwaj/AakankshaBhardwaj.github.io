---
layout: post
title: "Creating mime type alias in rails"
modified:
categories: blog
excerpt:
tags: []
image:
  feature:
date: 2015-08-01T15:39:55-04:00
comments: true
---

Hello Friends,

Today I am going to discuss about the mime type alias in rails. How ever in practice we need to show
multiple views according to the request. Like if request is comming from web(html) then you just show
the html page, if request is coming from mobile then show the mobile view. Its very esay to handle this
situation in rails applications by mime type alias. Here is an example of doing so:

###Creating mime type
The first step is to create a mime type alias of your type(mobile,ipad or anything else) for this
write the following lines in the ```config/initializers/mime_types.rb``` file

{% highlight ruby %}
Mime::Type.register_alias "text/html", :your_alias #like (:mobile,:ipad etc).
Mime::Type.register_alias "text/javascript", :your_alias
{% endhighlight %}


###Create views
Now create views of the requested action by ```action_name.your_alias.erb``` inside your controller's view.

###Request
Now if you request your actions with the ```formats: :your_format``` then rails will serve ```action_name.your_alias.erb```
as view.

####Note
Please keep in mind that after changing in initializers requires a server restart so don't forget to restart your server.
