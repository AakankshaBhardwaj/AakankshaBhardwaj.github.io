---
layout: post
title: "Invalid Authenticity Token"
modified:
categories: blog
excerpt:
tags: []
image:
  feature: 
date: 2015-09-12T15:39:55-04:00
comments: true
---
To protect your application from hackers,rails includes a built in mechanism for preventing CSRF(Cross-Site Request Forgery), protect_from_forgery method.

Rails creates cryptographically random tokens,which are bounded to the user's session.Within each form a hidden input field,authenticity_token,is injected;this field contains the synchronizer token.The token is sent with the form submission request and is processed by the web application.

When processing the request,the server compares the value submitted by the authenticity_token parameter to the value associated with the user's session.If it doesn't match,this indicates the request may be a malicious request forged by the attacker.In this case.it is expected that the request will fail , protecting the application from CSRF.

##STEPS:

1) Protect from forgery method calls verify_authenticity_token.

2) The request is verified.

3) If the request is valid it is executed.

4) If the request is invalid it is handled by  handle_unverified_request method.

5) Session reset.

###reset_session method
{% highlight ruby %}
session.destroy if session && session.respond_to?(:destroy)
self.session = {}
@env['action_dispatch.request.flash_hash'] = nil
{% endhighlight %}