---
layout: post
title: "Creating a circular progress Bar by using SVG path"
modified:
categories: blog
excerpt:
tags: []
image:
  feature:
date: 2015-05-16T15:39:55-04:00
---

Hi Friends,
 
This is my first post here.I tried to make a circular progress bar in my application and I done it by using SVG Path.

Here is the sample code,

### HTML
{% highlight html %}
<svg style="width:100%; height:100%; position:absolute; top:0; left:0;">  
    <path d="M200,200 " id="arc" fill="none" stroke="green" stroke-width="20"/>
</svg>
{% endhighlight %}

In path tag 'd=M200,200'  where (200,200) is the starting point from where the circular bar start.

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
