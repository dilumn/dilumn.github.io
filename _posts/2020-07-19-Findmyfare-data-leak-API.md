---
author: dilumnavanjana
layout: post
title: "Findmyfare data leak API"
date: 2020-07-19 21:00
comments: true
category : security
tags:
- security
---

Yes this time it is [Findmyfare.com](https://www.findmyfare.com/)

Recently I found two issues in Findmyfare website. So as usual I reported the issues. Unlike Dialog & Mobitel, Findmyfare was very responsive & took it very seriously. Within few hours after I reported issues, they deployed 1st issue fix & a patch for the 2nd issue (Not exactly a fix, but data leaking issue was gone).

In this blog post I will explain what were those two issues.

### First issue

This looks more like a mistake. But this kind of mistake can be easily identify from code reviewing (Not sure they do code review or not). Anyway the issue was, they returned account activation url to frontend once user register in their system.

<img height="600" width="800" style='border:3px solid #000000' src="{{ site.url }}/images/findmyfare-1.png"/>

So someone could register in Findmyfare.com with a random email address which is not belong to that user, and get his account activated using activation url return from register API response. He doesn't need to have access to the Verify Account email because of this issue. Not that serious because of Findmyfare business model but something they could noticed easily.


<iframe src="https://www.youtube.com/embed/17WVczKalK8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### Second issue

This one is bit more serious. Everytime you book a flight using Findmyfare as a logged in user, they save your traveller data in their db. If you book for multiple people, all those traveller information get saved. You can see those saved traveller information from Findmyfare user profile page.

<img height="600" width="800" style='border:3px solid #000000' src="{{ site.url }}/images/findmyfare-2.png"/>


And then you can edit traveller information, so next time when you book a flight edited information will be applied.

<img height="600" width="800" style='border:3px solid #000000' src="{{ site.url }}/images/findmyfare-3.png"/>

When a user click edit button & open popup, frontend fetch traveller information from backend to popupate fields.

```
Endpoint information

POST https://www.findmyfare.com/account/user_co_traveller/re_populate

Body
id - traveller_id
csrf_fmf_secure - some token

```

Only logged in users can call this endpoint, Findmyfare uses a cookie based authentication for this. But they missed to authorize the user requesting traveller data. Basically any logged in user of Findmyfare could request any traveller information because Findmyfare didn't check whether traveller data requested by the user actually belong to that user or not. So this endpoint leaked an entire database table of Findmyfare system.

#### How big was the issue

There are currently more than 75,000 traveler data in Findmyfare system. Could be a nice set of data for a travel agency in Sri Lanka to do marketing. That user data includes,

```
traveler id
user id
user type
first_name
last_name
date of birth
mobile number
email
address
country
passport
passport issue place
passport expiry date
frequent flyer airline
frequent flyer no
meal preference
preferred seat
price range
```

They added a patch to this `re_populate` API & now it doesn't return any user data even though traveler data belong to logged in user. Hopefully they will enable this endpoint to return user data, but only traveler data belong to logged in user.

<iframe src="https://www.youtube.com/embed/Ef90arGgpis" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Cheers,<br>
DilumN
