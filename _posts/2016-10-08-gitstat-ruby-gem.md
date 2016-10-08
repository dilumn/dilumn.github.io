---
author: dilumnavanjana
layout: post
title: "gitstat Ruby gem & it's usage"
date: 2016-10-08 21:00
comments: true
category : ruby
tags:
- ruby
---

Gitstat is a ruby gem for `git log` your repository to get commit history by number of lines for each Author in your repository

# Installation

`$ gem install gitstat`

# Usage

After installing the gem, go to your repository & just type `gitstat`. Then you will get the total number of added lines / deleted lines & commits by each author in the repository.

{% highlight java %}
Author >>>>  //de
lines added: +11839 lines    |   deleted: -16271 lines   |   total commits: 368
************************************************************************************

Author >>>>  Adrian Hosey
lines added: +52 lines   |   deleted: -10 lines    |   total commits: 2
************************************************************************************

Author >>>>  Alex Grigorovich
lines added: +3 lines    |   deleted: -1 lines   |   total commits: 1
************************************************************************************

{% endhighlight %}

To get total number of added lines / deleted lines & commits by each author in a given period,

`gitstat -t 05/22/2015 04/30/2016`


To get total number of added lines / deleted line & commits by author

`gitstat -a AUTHORNAME`


More features coming soon.....

Cheers,

BC_Dilum
