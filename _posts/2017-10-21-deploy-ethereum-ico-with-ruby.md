---
author: dilumnavanjana
layout: post
title: "Deploy Ethereum ICO with Ruby"
date: 2017-10-21 21:00
comments: true
category : ethereum
tags:
- ethereum
---

I am using a Docker image that I optimized to use for ruby Development. Have a look at the [ethereum-rb](https://hub.docker.com/r/dilumn/ethereum-rb/) & also if you want to see the [Dockerfile](https://github.com/dilumn/ethereum-rb).

Everything I am describing here are in [ico-rb](https://github.com/dilumn/ico-rb) repository. To get started clone the repository. So it will be easy for you to understand better.

Then `docker-compose build` will fetch all dependencies & install.

`docker-compose -f docker-compose.yml up` will start running the `ethereum` network in the container. If you are running this for the first time, it will take few hours to sync all blocks to your container. Make sure you are fully synced with the Ethereum network before deploying your smart contract.

There are several Ethereum test networks for your testings. By default this repository is pointing to `rinkeby` ethereum test network. But if you want to run the main `ethereum` network remove `command: --rinkeby` line from `docker-compose.yml`

After you are done with syncing the blocks of the network, you are good to go with deploying the smart contract. But to deploy a smart contract you must have a `ethereum` account with some ethereum coins. Because it will cost a few amount to deploy a smart contract. You can login to `geth` console of the container using this command.

`docker exec -it CONTAINERNAME geth attach ipc:/root/.ethereum/rinkeby/geth.ipc`

If you are connecting to the main `ethereum` network, `docker exec -it CONTAINERNAME geth attach` will be enough

After connecting to the `geth` console, you can create a new account from this command `personal.newAccount("PASSPHRASE")`. Add whatever the passphrase you want within quotation. Before deploying a smart contract you have to unlock this account using the PASSPHRASE. `personal.unlockAccount("ACCOUNTNUMBER")`. You can have a look at other eth commands too. Before deploying the smart contract, make sure you have some amount of `ethereum` for this account. You can get free `ethereum` coins for rinkeby network from [crypto faucet](https://www.rinkeby.io).

Now the final stage of deploying the smart contract. First bash into the container using `docker exec -it CONTAINERNAME bash`. And the sample app you downloaded from the repository is in the app directory. In the app directory `bundle install` & run the ruby script `bundle exec ruby contract_sample.rb` This final command will connect to the ethereum node & deploy your smart contract. Normally it will take about 1 minute to deploy the smart contract.

For this I'm using [ethereum.rb](https://github.com/EthWorks/ethereum.rb) gem to compile & deploy the smart contract.

Cheers,

DilumN
