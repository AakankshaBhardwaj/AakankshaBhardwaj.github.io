---
layout: post
title: "Difference between rails app deployment tools mina and capistrano"
modified:
categories: blog
excerpt:
tags: []
image:
  feature:
date: 2015-07-18T15:39:55-04:00
comments: true
---

Every web application needs to be deployed to a server at one point, and there are several ways to do that. If you are
running Rails server, what's the best way to do that?

you ever needed to deploy a Ruby on Rails application to a VPS or dedicated server, I bet you used Capistrano, 
a deployment tool used by many developers around the world. We used it as well, but then we met Mina.

### What's wrong with Capistrano?
Maybe you're wondering what's wrong with Capistrano. Doesn't it do the job? Yes, it does, and yes, it's great, but it's
also terribly slow.Capistrano deployments can take up to 3 minutes if, for example, you have a large repository,
if you've changed a couple of database columns or made some extensive changes to the applications. If you deploy all
day, every day, being slow isn't an option for you.
Well... we deploy every day, and Capistrano just wasn't working for us anymore, so we began to search for a better
solution. At that time, the guys from Dwellable wrote an article about the most recent RailsRumble event and analyzed
the most popular gems used by the competing developers. It turns out that 13% of the competing teams used Mina and
that was reason enough for us to check it out.

### Capistrano vs Mina
To show the difference between these deployment tools, we measured their performance on two different projects.
####CAPISTRANO
Steps we had to perform:

* Add gem ```capistrano``` and gem ```capistrano-rails``` to the Gemfile.
* Call ```cap install```
* Edit the ```deploy.rb```, ```Capfile``` and ```production.rb``` file.
* Call ```cap production deploy:cold``` to deploy.
Because Capistrano only records the time for every command it runs, we can't see how long the whole deployment takes.
Luckily, my trusty phone has a stopwatch, so I recorded the elapsed time on my own. And the result - the deployment
process with Capistrano took 180 seconds of our precious time.

So let's do it again, but this time with Mina.

####MINA

The first thing that we noticed on Mina website was the title Really fast deployer and server automation tool, and that
alone put a smile on our faces.Again, we created a new project and pushed it to a repository. After adding the
gem ```mina``` to the ```Gemfile```, it was very easy to configure the ```deploy.rb``` file, and, in less than a
minute, we were ready to deploy (note that the repository size was around 250 KB).

We performed these steps:

* Add gem ```mina``` to the ```Gemfile```
* Call ```mina init```
* Edit the ```deploy.rb``` file
* Call ```mina setup```
* Call ```mina deploy```

###Conclusion
Mina is usefull when you are doing a frequent deployment to the server. Both mina and Capistrano took approx same time to 
perform a fresh deployment. The difference is to deploy next time where mina take approx 5 sec to deploy where capistrano
took the same time as fist time
