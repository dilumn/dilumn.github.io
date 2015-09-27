---
author: dilumnavanjana
layout: post
title: "Celluloid Async Tasks"
date: 2015-09-27 21:00
comments: true
category : celluloid
tags:
- celluloid
---

Most of Ruby developers use `celluloid` because it's very easy to use for asynchronous tasks. If someone want to do a process in background they can simply do it by one keyword. The keyword is `async`.

Here is a simple example to show the usage of `Async` feature.

{% highlight bash%}
require 'celluloid/current'

class Rocket
  include Celluloid
  
  def launch
    for i in 0..5
      sleep 2
      puts "Counting.....#{i}"
    end
    puts "Blast off"
  end
end

rocket = Rocket.new

rocket.async.launch
{%endhighlight%}

That `launch` method is running in the background.


Cheers,
BC_Dilum
