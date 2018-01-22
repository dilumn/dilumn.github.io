---
author: dilumnavanjana
layout: post
title: "I am converting Bitcoin blockchain to SQL"
date: 2017-11-04 21:00
comments: true
category : bitcoin
tags:
- crypto
- bitcoin
---

Recently I developed a Ruby wrapper gem for Bitcoin & Ethereum RPC APIs. Using that I started converting Bitcoin transactions to a SQL format just for fun. My plan was to query the transactions easily to get some stats about the transactions that people did in the past few year. I thought it would be maximum 1 week task to convert all transactions which were in 500K+ blocks by that time. But by the time I write this blog post, I am still running the script.

Until the first 100K blocks I used a very simple Ruby script that iterate through blocks, get informations about transactions & write them to the SQL table one transaction by one. But later I realized writing one by one to SQL table is not an efficient thing. So I modified my script to support bulk insert to the SQL table. Right now the script is writing to the table 500 transactions once. It was faster than the previous implementation, but still it will take few weeks to finish this operation.

If you want to have a look at the Ruby gem I developed & used to connect to Bitcoin RPC APIs, here is the [elchapo](https://github.com/dilumn/elchapo) gem.

I used a simple Ruby script to convert the transactions to a SQL table. Initially I thought I will be able to finish converting all transactions within 5 days with the testing I did with the `testnet` network. But I was wrong. A real Bitcoin block contains so many transactions than a block in `testnet`. So after running the Ruby script for two weeks, I managed to convert 14,852,781 transactions to SQL until 22/04/2013. Long way to go & number of transactions in a Block is keep increasing. Right now a Block contains at least 1000 transactions. So all the stats I have given below are limited to the first 3 years of the Bitcoin transactions. I will write another blog post once I finish converting  all the blocks.

If you don't know what is `testnet`, it is a test network for Bitcoin. It behaves as same as Bitcoin, but if you have `testnet` Bitcoins in your wallet it doesn't have any value. So usually developers can do testing with this `testnet` other than directly do transactions with the real Bitcoin network which is not a good way to test.

A block contains these information which we can extract from the RPC API,
<img height="600" width="800" style='border:1px solid #000000' src="{{ site.url }}/images/bt_block.png"/>

And a block can contain multiple transactions. Using those transaction ids, I can get the raw transaction details, which looks like this. I used these JSON responses to populate the SQL database.
<img height="600" width="800" style='border:1px solid #000000' src="{{ site.url }}/images/bt_transaction.png"/>

Here is my SQL table with columns I used to save converted data.
<img height="600" width="800" style='border:1px solid #000000' src="{{ site.url }}/images/bt_table.png"/>

With the transactions I have until 22/04/2013 from the day Bitcoin started, I queried to see what is the highest value transfered from a transaction. The value I got was unbelievable & I checked that transaction on `blockexplorer.com` too. But that value & the transaction is a valid one. `499,720.7` BTC were transfered from that transaction on 16/11/2011 which is on 153,527 Block. May be the owner of that wallet is `Satoshi`(creator of Bitcoin).

Here is that transaction on [blockexplorer](https://blockexplorer.com/tx/044e32f5e01d70333fb84b744cb936bf49acab518282c111894b18bcf3a63c12)

`blockexplorer.com` screenshot for that transaction.
<img height="600" width="800" style='border:1px solid #000000' src="{{ site.url }}/images/bt_highest.png"/>

More will come soon once I complete converting all transactions.

Cheers,

DilumN
