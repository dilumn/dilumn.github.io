---
author: dilumnavanjana
layout: post
title: "Create Celluloid Development Environment"
date: 2015-09-24 21:00
comments: true
category : celluloid
tags:
- celluloid
---

If you want to contribute to `Celluloid`, you are warmly welcome. For beginners here are the steps you should follow to setup your development environment.

1 - First of all `git clone` your Forked `Celluloid` source or clone directly from the main repository.

2 - Then create a new file named `Gemfile` wherever you want.

3 - Include this inside your `Gemfile`

{% highlight bash%}
source 'https://rubygems.org'

gem 'celluloid', :path => '~/Documents/celluloid'
{%endhighlight%}

 - The path here is your cloned source path.

 4 - You are ready to test `Celluloid` source with the changes you are doing, without push it to Github.

 {% highlight bash%}
bundle install
{%endhighlight%}
Run `bundle install` before running any Ruby classes you want to test.

After that create a Ruby class as you want & `bundle exec ruby example.rb` (here example.rb is your sample Ruby code).

It'll execute that Ruby class with including `Celluloid` from the local path. Then you can do any changes to the local `Celluloid` source & test them.

Cheers,
DilumN
