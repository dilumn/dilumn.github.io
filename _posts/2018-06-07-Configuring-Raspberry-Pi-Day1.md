---
author: dilumnavanjana
layout: post
title: "Configuring Raspberry Pi Day 01"
date: 2018-06-07 21:00
comments: true
category : raspberry
tags:
- raspberry
---

This is the first blog post of me about Raspberry Pi & planning to write posts about my Raspberry Pi configuration updates frequently. Yesterday while I was in my workplace, I got an idea to run a server for my personal use. Initially my plan was to run some daily tasks which are doing everyday. So for that I was thinking what is the best place to have a server which I can access. First of all AWS was the place came to my mind.

It will be the easiest solution for me. I can start a Micro Instance which will cost me about 10USD per month. But then I was thinking for a more cheaper option & Raspberry Pi was the next option came into my mind. Honestly I didn't have much idea or knowledge about Raspberry Pi at that time. So first of all I searched online whether I can install Ubuntu or Linux on Raspberry Pi. The search results I got were pretty good & in few minutes I realized that it is not a hard thing to install Linux version on a new Raspberry Pi.

Without thinking too much I decided to buy a Raspberry Pi because if I think too much I will not buy it later. So in few hours I managed to find a near by shop which sells them & on lunch time I went there to check the price.

Raspberry Pi 3 B+ was SGD 63 & Raspberry Pi 3 B was SGD 57. So I decided to buy B+ which had 1 GB Ram. So here are the things I managed to do within Day 01 with my new Raspberry Pi.

First problem came to me was Ubuntu 16.04 was not supported to my Model B+. I downloaded the image from [here](https://ubuntu-pi-flavour-maker.org/download/). But after few attempts I realized Ubuntu 16.04 is not supporting Model B+ yet. May be there are some other ways I could use.

Then I managed to download & install Raspbian image from [here](https://www.raspberrypi.org/downloads/raspbian/) which is also a Debian version. So this will be enough for my work as I think.

And as of basic things I created a new user for me & setup SSH Raspberry Pi with my personal laptop public SSH key. So no one else can SSH. But then I realized I can SSH in without any problem using the Ethernet port to Raspberry Pi, but not using wlan0. After searching for a solution I realized that I need to update my firmware. So after updating firmware I managed to SSH using wlan0 as well.

For the day 01, that's all I managed to do. Hope to explore more & install more packages soon & face new challenges while playing with Pi.


Cheers,<br>
DilumN
