---
author: dilumnavanjana
layout: post
title: "Finished converting Bitcoin Transactions"
date: 2018-03-17 21:00
comments: true
category : bitcoin
tags:
- crypto
- bitcoin
---

Few months ago I wrote a blog post about [I am converting Bitcoin blockchain to SQL](https://dilumn.github.io/bitcoin/2018/01/03/I-am-converting-Bitcoin-blockchain-to-SQL/). And gave several meet up talks about this crazy idea I had & the progress of the work.

### Ruby Meetup Singapore - Cryptocurrency & Ruby

<iframe width="560" height="315" src="https://www.youtube.com/embed/4QsBbnQ-n40" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

You can find the slides here on [Slideshare](https://www.slideshare.net/DilumNavanjana/cryptocurrency-ruby-elchapo-gem)

Here I am with the full database of transactions from the day Bitcoin started to March 2018. If you want to check how I did it look at my previous blog post on [I am converting Bitcoin blockchain to SQL](https://dilumn.github.io/bitcoin/2017/11/04/I-am-converting-Bitcoin-blockchain-to-SQL/)

### It took me more than 3 months to finish this conversion.

Yes I know the way I used to convert transactions is not the fastest way to do something like that. But I enjoyed a lot checking the progress everyday morning.

**Database size is 76.63 GB**

**236,915,620 transactions**

### Database columns
Block number <br>
Transaction hash <br>
Block hash <br>
Value (Transfered value) <br>
Created_at <br>
Sender <br>
Receiver <br>
Balance_receiver

Interesting facts found from the database,

### Highest transaction value by year

**Within 2009** - 6000 BTC
<br>
Transaction on <a href="https://blockexplorer.com/tx/123a3968cd91b42cc1ecfb3d0d11e5b09d21e923344847a1e4b2577d3bbc69a2" target="_blank">blockexplorer</a>

**Within 2010** - 90,000 BTC
<br>
Transaction on <a href="https://blockexplorer.com/tx/1ec28eee10a0fc07fcad63803c785cf98df2e7f2184705208b744254d60cca08" target="_blank">blockexplorer</a>

**Within 2011** - 499,720.7 BTC
<br>
Transaction on <a href="https://blockexplorer.com/tx/044e32f5e01d70333fb84b744cb936bf49acab518282c111894b18bcf3a63c12" target="_blank">blockexplorer</a>

**Within 2012** - 125,000 BTC
<br>
Transaction on <a href="https://blockexplorer.com/tx/7e79124b35a5b6477a6d3e9cfda2e4635e2d12578dfb48a2b739bf0d348b24af" target="_blank">blockexplorer</a>

**Within 2013** - 194,993 BTC
<br>
Transaction on <a href="https://blockexplorer.com/tx/1c12443203a48f42cdf7b1acee5b4b1c1fedc144cb909a3bf5edbffafb0cd204" target="_blank">blockexplorer</a>

**Within 2014** - 212,517.634 BTC
<br>
Transaction on <a href="https://blockexplorer.com/tx/9d25b5eaa65de602fe6a11ba9db83f3b1105899b12664f3302a5ccf1cff955d8" target="_blank">blockexplorer</a>

**Within 2015** - 94,772 BTC
<br>
Transaction on <a href="https://blockexplorer.com/tx/0d8aab8a54a805cab48505449d1c4adb40ff012dd6e301f44f71116d4993f755" target="_blank">blockexplorer</a>

**Within 2016** - 50,490 BTC
<br>
Transaction on <a href="https://blockexplorer.com/tx/7e03b97481d09e22c89c6ad35b46f605b1df2c36d2fe7434ba561ee3bbbe3479" target="_blank">blockexplorer</a>

**Within 2017** - 50,000 BTC
<br>
Transaction on <a href="https://blockexplorer.com/tx/4991215e87ed06d6f83a30dcca806b6148a3c2d3ad4f114bff60e4f6e86dc5bf" target="_blank">blockexplorer</a>


### All time highest value transfered is 499,720.7 BTC on 16/11/2011
<a href="https://blockexplorer.com/tx/044e32f5e01d70333fb84b744cb936bf49acab518282c111894b18bcf3a63c12" target="_blank">blockexplorer</a>

### But the highest value in USD transfered is 50,000 BTC on Aug 2, 2017, because BTC/USD value on that day is about $2700 & that transaction in USD is about $135,000,000
<a href="https://blockexplorer.com/tx/4991215e87ed06d6f83a30dcca806b6148a3c2d3ad4f114bff60e4f6e86dc5bf" target="_blank">blockexplorer</a>


Sorry I couldn't find any place to upload this huge db for free. So I decided not to upload it. But I can share the Ruby script that I used to convert.


Cheers,<br>
DilumN
