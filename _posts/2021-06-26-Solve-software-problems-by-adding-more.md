---
author: dilumnavanjana
layout: post
title: "Solve software problems by adding more"
date: 2021-06-26 23:00
comments: true
category : programming
tags:
- programming
---

It was a Saturday morning. I was watching Youtube & saw this video on Youtube.

<iframe width="560" height="315" src="https://www.youtube.com/embed/-VCGPiQINMQ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Immediatly few examples from my day to day work came in to my mind.

Few week ago I was fixing a small edge case bug in one of our products. Even before starting to fix the issue, I knew it will be one line of code change. So I did the fix & next day here come the QA report, because of that one line change I did, I have introduced 4 more edge cases which cause some inconsistancies. Then I started fixing those issues one by one, few hours later I managed to fix everything, but with several changes to the existing structure. In which there were few new local variables, added an optional parameter to a method, added one new state.

I started thinking is it worth all these new additions & added complexity for a small edge case bug. For few minutes I was thinking of negotiating with product team not to fix the initial edge case. Because it was not a critical bug & only cause UI inconsistency.

Then I revisited the initial bug & started from the begining again. Because now I know if I do one line change it will introduce few more edge cases, I took a different approach & managed to fix the initial bug without introducing any edge cases. Most importantly no new local variables or method parameter changes or new states. I continued thinking about what happened that day & even though it ended up well, there was a high chance I could have gone with all additional changes without realising there was a better way. So when I watched this Youtube video today morning, I knew that is exactly the same thing happened to me. I continued building more pieces without realising removing the first piece is the better solution.

So we can relate this brain function of adding pieces rather than removing pieces in software development. For example there is this library A, which is great at doing xyz than the current library B we are using. So we start using library A & realise one of the drawbacks of library A is performing abc action is slower than Library B. So we introduce library C to optimise it. There are cases still follow this chain benifits overall. But there can be other possible solutions rather than keep adding new libraries. Most of the time we miss those options because we love adding things rather than removing.

One more example I can think of (some of you will not agree with this), years ago we wanted our web applications to render html dynamically & didn't want to refresh whole page everytime user go to a new page. So we keep building our frontend frameworks, decade later we load hundred thousand lines of javascript to frontend for a web application to run smoothly & god knows what they do.


<br>
Cheers,<br>
DilumN
