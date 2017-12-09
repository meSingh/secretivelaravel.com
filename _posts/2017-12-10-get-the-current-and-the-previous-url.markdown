---
layout: post
title:  "Get the current & the previous URL"
date:   2017-12-10 16:36:45 +0530
categories: 
  - helpers
tags: 
  - url
  - helpers
---
There are times when we need to redirect a user back to its previous URL or when we need to check what the current URL is to confirm some trick actions.

Until now, we have been doing this using various complicated PHP core functions but Laravel makes it all very easy for us. You can use the following code for doing so.
Get the current URL

## Get the previous URL

{% highlight php %}
url()->previous()
{% endhighlight %}

## Get the current URL

{% highlight php %}
url()->current()
{% endhighlight %}
