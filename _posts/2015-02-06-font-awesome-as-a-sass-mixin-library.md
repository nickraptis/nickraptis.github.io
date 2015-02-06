---
layout: post
title:  "Font Awesome as a SASS mixin library"
date:   2015-02-06 23:50:20 +0200
categories: web
---
Here is a fun little project I did a while ago.
What if you wanted to use only a small subset of
Font Awesome instead of the whole thing?
And tidy up your HTML classes while you are at it?

[Font-Awesome](http://fontawesome.io/) is a much beloved toolkit
for bringing high quality icons to websites. If you never heard of it,
you should really check it out.

Font-Awesome works a lot like [Bootstrap](http://getbootstrap.com/):
Point to a CDN to include the library, then add classes to your HTML
elements to make a beautiful layout, or in this case, a cool icon.

{% highlight html %}
<i class="fa fa-camera-retro"></i>
{% endhighlight %}

However, again much like bootstrap, try to style things a bit too much
and you can easily end up with 5 or 6 or 10 classes in your elements.

{% highlight html %}
<i class="fa fa-quote-left fa-3x pull-left fa-border"></i>
{% endhighlight %}

Moreover, because you'd want them consistent, you would repeat those
same classes over and over again.
And it's a tradeoff, but HTML classes shine best when they are semantic
rather than ways to apply style.

So, what if you could mix the Font Awesomeness into your css behind the scenes?

At the time I was exploring the [Bourbon](http://bourbon.io/) and
[Neat](http://neat.bourbon.io/) libraries I heard about listening
to [Sean Devine](https://twitter.com/barelyknown) on the
[Ruby on Rails podcast](http://5by5.tv/rubyonrails).
Those work as mixin libraries that you can use with SASS to output
your stylesheets. It is a lot more involved process, but pays by leaving your
HTML cleaner in the end.

Enter **[Font Awesome SASS mixins](https://github.com/nickraptis/font-awesome-sass-mixins/)**
=============================================================================================

a variation of the Font Awesome source code that lets you treat it as
a SASS library, much like you would do with Bourbon.
It also works great in Jekyll ;)

It is really not much more than a one evening hack where I prefixed all `fa-`
classes as `@mixin fa-mx-`, and then fixed the cases where that wouldn't work
in the new context.
90% of the original code is left unchanged, and the sheer fact that I was able
to do it speaks volumes about how clean and well organized the original code is.

If anyone is interested in how you can use it, my next post will probably be some
examples. But even if I'm the only one using it, it was a fun little thing to make.
