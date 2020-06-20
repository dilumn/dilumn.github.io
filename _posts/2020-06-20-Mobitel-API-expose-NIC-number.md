---
author: dilumnavanjana
layout: post
title: "Mobitel API expose NIC number"
date: 2020-06-20 21:00
comments: true
category : security
tags:
- security
---

This is a story about a form validation. I already informed Mobitel (one of the telecommunication company in Srilanka) about this form validation more than two weeks ago by,
- Sending them two emails
- Contact them via Facebook fan page
- Via one of my friend who is working in Mobitel

But they haven't replied to me or change the form validation. So I thought "ok then. it is not a bug, it is a feature" & decided to write a blog post about that particular form validation.

Here is the form that I am going to talk here. I think it is something to do with changing Sim card.

<img height="600" width="800" style='border:1px solid #000000' src="{{ site.url }}/images/mobitel-1.png"/>

So it looks like before someone submit this form they need to validate 4 of these field data user entered. So they are using 4 API calls, 1 for each text box to validate the form. 4 API calls 😬😬

In first API call they send mobile number to backend & check whether it is correct or not. Then in the second API call they send only mobile number again to validate the NIC number. Yes they only send mobile number to validate NIC. How? That is the question I had when I saw the behaviour first time.

They only send mobile number in NIC validation API call & it returns the NIC number registered to the user entered mobile number. And frontend do the validation of NIC correct or not. That means anyone can go to this Sim Change form & enter anyone's mobile number & see the registered NIC number for that sim card.


Hope no one will use NIC validation API to go through all Mobitel numbers & download registered NIC numbers. Just saying!!


Cheers,<br>
DilumN
