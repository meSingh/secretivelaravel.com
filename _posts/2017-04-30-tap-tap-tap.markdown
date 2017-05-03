---
layout: post
title:  "Tap, Tap, Tap"
date:   2017-04-30 16:36:45 +0530
categories: 
  - helpers

# optional alternate title to replace page.title at the top of the page
#alt_title: "Basically Basic"

# optional sub-title below the page title
#sub_title: "The name says it all"

# optional intro text below titles, Markdown allowed
#introduction: |
#    Basically Basic is a Jekyll theme meant to be a substitute for the default --- [Minima](https://github.com/jekyll/minima). Conventions and features found in Minima are fully supported by **Basically Basic**.

tags: 
  - tap
  - helpers
  - higher order


#image:  # URL to a hero image associated with the post (e.g., /assets/page-pic.jpg)
#read_time: false
#comments: true  # disable comments on this post
---
Tap might be the most simplest helper of Laravel yet if used more often can help you write a more cleaner and readable code. Quite offen I find myself writing long strings of code just to modify a variable in some form. Honestly, it always end the same way, the dirty way. 

What ```tap()``` do's is, it takes a variable as it's first argument and then passes it through the callback given as 2nd argument. A typical example of tap, as used by Laravel is: 

{% highlight php %}
<?php

public function create(array $attributes = [])
{
    return tap($this->newModelInstance($attributes), function ($instance) {
        $instance->save();
    });
}
{% endhighlight %}

[Just recently][tap-code], Tylor has improved this tiny little helper to support shorten ```tap()``` calls even more. He call's it [HigherOrderTapProxy][tap-proxy]. It lets you pass an object to tap and then tap it's methods to return the object itself, for e.g. we can use tap to update a model record and return the object itself instead of a boolean value. 

{% highlight php %}
<?php

return tap($user)->update([
    'name'  => $name,
    'age'   => $age,
]);

{% endhighlight %}

[Tylor wrote a post][tap-tap-tap] on this tiny little helper and said:
> While ```tap``` is a very simple helper, I find it often lets me write terse, one-line operations that would normally require temporary variables or additional lines.



PS: I know, I copied title from original Taylor's post but after reading it, I just coudn't help it. It stuck in my mind. :P

[tap-code]: https://github.com/laravel/framework/blob/master/src/Illuminate/Support/helpers.php#L877
[tap-proxy]: https://github.com/laravel/framework/blob/master/src/Illuminate/Support/HigherOrderTapProxy.php
[tap-tap-tap]: https://medium.com/@taylorotwell/tap-tap-tap-1fc6fc1f93a6
