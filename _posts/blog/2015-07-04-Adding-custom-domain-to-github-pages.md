---
layout: post
title: "Adding custom domain to github pages"
modified:
categories: blog
excerpt:
tags: []
image:
  feature:
date: 2015-07-04T15:39:55-04:00
comments: true
---

Hi Friends,

However in practice you want to point your custom domain to your github pages.It quit simple to do that.
Here is the step by step description how to add a custom domain to your github pages. 
 
###Step 1
First of all go on GitHub, navigate to your Pages repository.
In the "Branches" menu, switch to your repository's Pages branch: 
* For User and Organization Pages sites, the Pages branch is ```master```.
* For Project Pages sites, the Pages branch is ```gh-pages```.

### Step 2
Add a new file, named ```CNAME``` to the root directory of the Pages branch.

###Step 3
In the new file, add a single line that specifies the bare subdomain for your custom domain.
For example, use ```example.com```, not ```https://example.com```. Note that there can only be one domain in the 
```CNAME``` file.

###Step 3
Commit the file

###Step 4
Confirming that the custom domain has been configured correctly
* In your repository's right sidebar, click setting tab. 
* Under ```GitHub Pages```, you should see the custom domain from your ```CNAME``` file.

###Step 5 (Configuring DNS settings)
After you've created and committed your ```CNAME``` file on GitHub, do one of the following with your DNS provider:
* If your custom domain is a subdomain (recommended), configure a ```CNAME``` record.
* If your custom domain is an apex domain, configure an ```ALIAS```, ```ANAME```, or ``A``` records.
    
####Example(Configuring DNS settings Bigrock)
* Login to your Bigrock account and go to your domain's ```DNS Management``` section.
* Click on ```Manage DNS```.
* Click on ```A Record``` tab.
* Click on ```Add A Record```.
* In Host Name write ```@```.
* In ```Destination IPv4 Address``` write ip ```192.30.252.153```.
* Finally click on add record button.

Now open your github page and you can see that it is forwarding to ```example.com```.

Hurray !!! you have successfully added your custom domain to your github page.

If more detail please [click here](https://help.github.com/articles/adding-a-cname-file-to-your-repository/).
