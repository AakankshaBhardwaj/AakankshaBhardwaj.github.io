---
layout: post
title: "How to deploy on heroku"
modified:
categories: blog
excerpt:
tags: []
image:
  feature:
date: 2015-00-17T15:39:55-04:00
comments: true
---

###To deploy rails application on heroku all you need to do is follow these steps:
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
c)$git push heroku master
{% endhighlight %}

Note: If you are using sqlite3 gem,you'll get an error while deploying
Gem::Installer::ExtensionBuildError: ERROR: Failed to build gem native extension.
remote:        
remote:        /tmp/build_f075a059a032a76b55f31bd152307fe1/vendor/ruby-2.0.0/bin/ruby extconf.rb
remote:        checking for sqlite3.h... no
remote:        sqlite3.h is missing. Try 'port install sqlite3 +universal',


###To solve this problem


{% highlight ruby%}
group :development :test do
gem 'sqlite3'
end
group :production do
gem 'pg'
end
{%end highlight%}


Thanks for reading this. 
