---
layout: post
title: "How access controller method in models"
modified:
categories: blog
excerpt:
tags: []
image:
  feature:
date: 2015-09-19T15:39:55-04:00
comments: true
---
##To implement log_rotate in rails application
###step 1: create a file in recipes folder as log_rotate.rb
{%ruby highlight%}
namespace :log_rotate do
  desc 'Install log_rotate template'
  task :install => :environment do
    queue! %[echo "#{erb(File.join(__dir__, 'templates', 'log_rotate.erb'))}" > /tmp/log_rotate]
    queue! %[sudo -A mv -f /tmp/log_rotate /etc/logrotate.d/#{application}_log_rotate.conf]
  end
end
{%end highlight%}
###Step 2: In your  /template directory create a file log_rotate.erb
{%ruby highlight%}
<%= File.join(deploy_to, current_path) %>/log/*.log
{
daily
size = 25M
missingok
compress
delaycompress
notifempty
copytruncate
}
{%end highlight%}
####Size
Log files are rotated when they grow bigger then size bytes.  If
                   size  is  followed by M, the size if assumed to be in megabytes.
                   If the k is used, the size is in kilobytes. So  size  100,  size
                   100k, and size 100M are all valid.
####compress
Old  versions  of log files are compressed with gzip by default.
####missingok
If the log file is missing, go on to the next one without  issuing an error message
####daily 
Log files are rotated every day.   
####delaycompress
Postpone  compression of the previous log file to the next rotation cycle.  This has only effect when used in combination with compress.
####notifempty
Do not rotate the log if it is empty 
####copytruncate
Truncate  the  original log file in place after creating a copy,instead of moving the old log file and optionally creating a new one.
###Step 3: In your lib/task directory create a file log_rotate.rake
{% highlight ruby %}
namespace :log_rotate do
desc "Cleanup application logs older than 30 days"
task :logs => :environment do
  `sudo /usr/sbin/logrotate -f /etc/logrotate.conf`
  puts("created logrotate")
end
end
{% endhighlight %}

###Step 4:In your deploy.rb file
Now you can access the controller's method inside the model by using
{% highlight ruby %}
Include log_rotate in your recipes
{% endhighlight %}



###Note: To test in your system
Create a file abc.conf in /etc/logrotate.d
####cd /etc/logrotate.d
####cat abc.conf
####$ /usr/sbin/logrotate -f /etc/logrotate.conf
This will rotate your logs.
