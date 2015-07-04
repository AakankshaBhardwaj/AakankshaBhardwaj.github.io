---
layout: post
title: "Read/Write operations with google drive"
modified:
categories: blog
excerpt:
tags: [google-drive]
image:
  feature:
date: 2015-06-20T15:39:55-04:00
comments: true
---

However in practice, we need read/write operations with google drive.In ruby it's pretty simple to perform 
read/write operations in google drive.Here is an example of the same using ruby script.  

### Prerequisite
To perform read/write operation use gem [google-drive-ruby](https://github.com/gimite/google-drive-ruby).

####Install gem
Run the following command 
{% highlight ruby %}
 sudo gem install google_drive
{% endhighlight %}

####Create a developer client_id and client secret
To create client_id and client_secret you have to follow these steps:

* Login to the Google's [Admin pannel](https://console.developers.google.com).
* Create a project and go to Api & auth tab.
* Click on credentials tab and click on 'Create new client ID'.
* Select Application type Web and give the callback url.
* Click 'Create Client ID'.

####Example to read/write files in Google Drive:
{% highlight ruby %}
require "google/api_client"
require "google_drive"

#=>Get an google api client
client = Google::APIClient.new
auth = client.authorization
auth.client_id = "YOUR CLIENT ID"
auth.client_secret = "YOUR CLIENT SECRET"
auth.scope = [
  "https://www.googleapis.com/auth/drive",
  "https://spreadsheets.google.com/feeds/"
]

auth.redirect_uri = "YOUR_REDIRECT_URL"
print("1. Open this page:\n%s\n\n" % auth.authorization_uri)
#=>This will print an url on screen.Copy this url and open in browser then copy the value of variable code and paste on the stdin.
print("2. Enter the authorization code shown in the page: ")
auth.code = $stdin.gets.chomp
auth.fetch_access_token!
#=> Get the access code
access_token = auth.access_token

#=> Get session
session = GoogleDrive.login_with_oauth(access_token)

#=> Gets list of remote files.
session.files.each do |file|
  p file.title
end

#=> Uploads a local file.
session.upload_from_file("/path/to/hello.txt", "hello.txt", convert: false)

#=> Downloads to a local file.
file = session.file_by_title("hello.txt")
file.download_to_file("/path/to/hello.txt")

#=> Updates content of the remote file.
file.update_from_file("/path/to/hello.txt")
{% endhighlight %}

For more details and to see an  example please refer this [link](https://gist.github.com/ramlaxmanyadav/8ad74896fe1172acc6c6)
