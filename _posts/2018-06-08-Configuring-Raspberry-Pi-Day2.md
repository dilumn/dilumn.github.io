---
author: dilumnavanjana
layout: post
title: "Configuring Raspberry Pi Day 02"
date: 2018-06-08 21:00
comments: true
category : raspberry
tags:
- raspberry
---

So the second day of my Raspberry Pi configuration started. The plan was to finish installing all required packages & finalize the environment setup.

Started the day by SSH the Pi from by personal laptop, which is perfectly working now & I don't need to connect HDMI monitor or USB Keyboard.

After SSH, installed Git & Ruby successfully. Then tried to install `bundler` gem & realized Raspberry Pi date & time is not correct. Most probably the reason is the Local network I am using is blocking port 123. So it cannot sync the datetime automatically. For now as a workaround I manually updated the date time. But need to find a permanent fix for this. This issue will raise again after I restart the Pi most probably.

And then I started creating my `buddy` project, which is going to be my personal assistant. Already committed the initial project structure & pushed to Github. [Here](https://github.com/dilumn/buddy) is the repo. It's going to be a Ruby project with Rack server & I am going to use Docker.

Because my `buddy` project is based on Docker-Compose, I started installing Docker into my Pi. First few attempts got failed & started reading what was the problem & then found out that Docker is only supporting 64 bit ARM. Then only I realized the Raspbian OS I installed is a 32 bit one & still there are no official 64 bit OS released. All the forum discussions suggest that it will come soon, but no timeline yet.

So because of that issue I faced, realized that `buddy` project need to develop outside Docker environment at least until there is a 64 bit OS release for Raspberry Pi.

So within next few days I will restructure `buddy` & will continue working on the `buddy` development because the Raspberry Pi configuration is almost done. One last thing, today is Friday & I am going to keep my Raspberry Pi turn on over the weekend & test the reliability of it.

That's all for today. Will write another post as soon as I get new things updated.


Cheers,<br>
DilumN
