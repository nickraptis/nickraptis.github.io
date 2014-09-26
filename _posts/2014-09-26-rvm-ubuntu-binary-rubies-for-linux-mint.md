---
layout: post
title:  "RVM: Ubuntu binary rubies for Linux Mint"
date:   2014-09-26 17:25:40 +0300
categories: ruby mint
---
[RVM](http://rvm.io/), the Ruby Version Manager is a magnificent tool that lets
you manage different Ruby versions and gemsets. Kinda like python's virtualenv,
but on steroids. Pair it with [bundler](http://bundler.io/) and there is not
much you can't do if you want to work with multiple Ruby environments.

RVM uses what it calls `binary rubies` which are precompiled Ruby binaries,
for select popular distributions and Ruby versions. If it fails to find one,
it will fall back to installing anything it needs from your distribution's
packages and then compiling Ruby from source. This fallback is not optimal,
but it works. Binary rubies are faster and more convenient though.

Ubuntu and Debian both get the love of binary rubies.
However, Linux Mint does not, at least not *yet*.

If you try to install Ruby version 2.1.2 in Mint 17 with RVM you get this:
{% highlight console %}
$ rvm install 2.1.2
Searching for binary rubies, this might take some time.
No binary rubies available for: mint/17/x86_64/ruby-2.1.2.
Continuing with compilation. Please read 'rvm help mount' to get more information on binary rubies.
Checking requirements for mint.
{% endhighlight %}
which means that you would have to compile it.

However, Ubuntu 14.04 which is the base for Mint 17 *does* have a binary ruby.
So why not install that instead? Lets see what we can find.

Googling `binary rubies` gets us to [the repository in the RVM site](https://rvm.io/binaries/).
There is indeed a binary for 2.1.2 in the Ubuntu 14.04 folder.

Now, remember the comment in the console output above?
{% highlight console %}
Please read 'rvm help mount' to get more information on binary rubies.
{% endhighlight %}
Turns out that you can install a binary ruby directly from a url.
We copy the link for the ubuntu binary ruby and do
{% highlight console %}
$ rvm mount -r https://rvm.io/binaries/ubuntu/14.04/x86_64/ruby-2.1.2.tar.bz2
https://rvm.io/binaries/ubuntu/14.04/x86_64/ruby-2.1.2.tar.bz2 - #configure
ruby-2.1.2 - #download
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 22.8M  100 22.8M    0     0  1077k      0  0:00:21  0:00:21 --:--:-- 1142k
ruby-2.1.2 - #validate archive
ruby-2.1.2 - #extract
ruby-2.1.2 - #validate binary
ruby-2.1.2 - #setup
ruby-2.1.2 - #gemset created /home/airscorp/.rvm/gems/ruby-2.1.2@global
ruby-2.1.2 - #importing gemset /home/airscorp/.rvm/gemsets/global.gems....................................
ruby-2.1.2 - #generating global wrappers........
ruby-2.1.2 - #gemset created /home/airscorp/.rvm/gems/ruby-2.1.2
ruby-2.1.2 - #importing gemsetfile /home/airscorp/.rvm/gemsets/default.gems evaluated to empty gem list
ruby-2.1.2 - #generating default wrappers........
{% endhighlight %}
And now Ruby 2.1.2 is installed in RVM without needing to compile it.

Of course, RVM does only have the most popular versions precompiled.
If you can't find what you are looking for in their site, don't be afraid to
compile it anyway.

Have fun!
