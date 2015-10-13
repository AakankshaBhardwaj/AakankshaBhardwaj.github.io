---
layout: post
title: "How to Pass"
modified:
categories: blog
excerpt:
tags: []
image:
  feature:
date: 2015-08-22T15:39:55-04:00
comments: true
---
One reason to proxy to other servers from Nginx is the ability to scale out your infrastructure. Nginx is built to handle many concurrent connections at the same time. This makes it ideal for being the point-of-contact for clients. The server can pass requests to any number of backend servers to handle the bulk of the work, which spreads the load across your infrastructure. This design also provides you with flexibility in easily adding backend servers or taking them down as needed for maintenance.

Another instance where an http proxy might be useful is when using an application servers that might not be built to handle requests directly from clients in production environments. Many frameworks include web servers, but most of them are not as robust as servers designed for high performance like Nginx. Putting Nginx in front of these servers can lead to a better experience for users and increased security.

Here is an example of proxy pass in nginx:

The most straight-forward type of proxy involves handing off a request to a single server that can communicate using http. 
Example:
{% highlight ruby %}
location /some_url {
    proxy_pass http://example.com;
}
{% endhighlight %}

In the above configuration, no URI is given at the end of the server in the proxy_pass definition.
For definitions that fit this pattern, the URI requested by the client will be passed to the upstream server as-is.
when a request for ```/some_url/hello_url``` is handled by this block, the request URI will be sent to
the ```example.com``` server as ```http://example.com/some_url/hello_url```.

Sometimes, this kind of replacement is impossible. In these cases, the URI at the end of the proxy_pass definition
is ignored and either the original URI from the client or the URI as modified by other directives will be passed
to the upstream server.

For instance, when the location is matched using regular expressions, Nginx cannot determine which part of the URI
matched the expression, so it sends the original client request URI. Another example is when a rewrite directive is
used within the same location, causing the client URI to be rewritten, but still handled in the same block.
In this case, the rewritten URI will be passed.

Example of proxy pass with headers:
{% highlight ruby %}
location /learn {
rewrite   /learn(.*)$  $1/  break;
proxy_pass http://45.55.156.88:80;
proxy_set_header X-Real-IP $remote_addr;
proxy_set_header Host $host;
}
{% endhighlight %}

when a request for ```/some_url``` ,the request URI will be sent to the example.com server as ```http://example.com/some_url```.



Thanks for reading this. 

Enjoy!!!
