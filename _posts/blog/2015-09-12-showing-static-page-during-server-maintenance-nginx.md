---
layout: post
title: "How to show a static page during server maintenance by nginx ?"
modified:
categories: blog
excerpt:
tags: [nginx]
image:
  feature:
date: 2015-09-12T15:39:55-04:00
comments: true
---
Hello there! I am back again with the new blog post.All of us mush have faced the application maintenance
downtime over the production environment. Rather than making the whole application down and displaying
service not found you can serve any custom static page while maintenance. For this you have to make some
changes in your server configuration.Here is an example of handling this situation by nginx configuration.

###Make a custom static page you want to serve
First of all make a static page and push it inside the application's/current/public folder.

###Make a maintenance.html file inside the application's/shared/system
Make a file named ```maintenance.html``` inside the ```application's/shared/system``` directory.

###Edit nginx configration
Now edit the nginx configration add foolowing lines inside your nginx configration file located inside the
```/etc/nginx/site-enable/some_name```.

{% highlight ruby %}
error_page 503 @maintenance;

    location @maintenance {
    rewrite ^(.*)\$ /error_page_name.html break;
    }

    if (-f \$document_root/../../../shared/system/maintenance.html) {
    return 503;
    }

{% endhighlight %}
#=> After writing the above code nginx search for ```$document_root/../../../shared/system/maintenance.html``` file if the file exists then it will show the ```error_page_name.html``` which is inside your ```application's/current/public``` directory.

####Restart your nginx server
Now restart nginx by executing
```sudo service nginx restart ```

#=> Here we go, if there is a file named ```maintenance.html``` inside the ```application's/shared/system``` directory. It will show your error_page_name.html page.

Enjoy!!




