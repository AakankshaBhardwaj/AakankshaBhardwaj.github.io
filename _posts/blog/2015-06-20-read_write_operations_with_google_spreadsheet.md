---
layout: post
title: "Read/Write operations with google spreadsheet"
modified:
categories: blog
excerpt:
tags: []
image:
  feature:
date: 2015-06-20T15:39:55-04:00
comments: true
---

However in practice, we need read/write operations with google spreadsheets.In ruby it's pretty simple to perform 
read/write operations in google spreadsheets.Here is an example of the same using ruby script.  

### Prerequisite
To perform read/write operation use gem [google-drive-ruby](https://github.com/gimite/google-drive-ruby).

####Install gem

``` sudo gem install google_drive
### JavaScript

{% highlight javascript %}
function drawCircle() {
        var i = 0;
        var circle = document.getElementById("arc");
        var angle = 0;
        var radius = 30;    
        window.timer = window.setInterval(
        function() {
            angle +=5; 
            angle %= 360;
            var radians= (angle/180) * Math.PI;
            var x = 200 + Math.cos(radians) * radius;
            var y = 200 + Math.sin(radians) * radius;
            var e = circle.getAttribute("d");
            if(i==0) {
                var d = e+ " M "+x + " " + y;
            }
            else {
                var d = e+ " L "+x + " " + y;
            } 
            circle.setAttribute("d", d);
            i++;
        }
      ,100)
    }});  
{% endhighlight %}

Call drawCircle(); function onLoad or whenever required.drawCircle() create a circular progress bar that starts from point(200,200).
