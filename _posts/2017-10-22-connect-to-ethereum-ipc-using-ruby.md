---
author: dilumnavanjana
layout: post
title: "Connect to Ethereum IPC using Ruby"
date: 2017-10-22 21:00
comments: true
category : ethereum
tags:
- crypto
- ethereum
---

To make things easier, I'm using the same [ethereum-rb](https://hub.docker.com/r/dilumn/ethereum-rb/) docker image as my node. It is configured to run Ruby developments environment too. So I don't need to do any configurations in my personal computer to start Ethereum node. This is the docker-compose file I am using with the configurations.

---
docker-compose.yml

    version: '2'

    services:
      app:
        build: ./app
        command: --rinkeby --rpcapi "db,personal,eth,net,web3" --rpccorsdomain='*' --rpc --rpcaddr="0.0.0.0"
        volumes:
          - $HOME/.rinkeby:/root
          - ./app:/app

---

So you can have a folder `app` which contains my Dockerfile & pass `command` parameters to the `ethereum` node. By passing `--rinkeby` you can connect to the `ethereum` rinkeby test network & skip the main network for testing. And also you should have a volume to store the blockchain in local otherwise all the syncronized blocks will be gone after you stop the docker container.

And my Dockerfile is inside `app` folder.

---
Dockerfile

    FROM dilumn/ethereum-rb
    MAINTAINER Dilum Navanjana <dilumn@bbytes.sg>

---

You don't need to do any configuration in the Dockerfile because all the configurations are done in `docker-compose.yml`.

Then you can build & run your ethereum node which is connecting to `rinkeby` network in my example.

    docker-compose build
    docker-compose -f docker-compose.yml up

By running these two commands you can see the `ethereum` node start syncronizing the blocks & at first it will take few hours to finish the syncronization.

There are two ways to connect to a `ethereum` node from outside. One is `IPC` & other one is using `HTTP`. I will write a separate blog post about the `HTTP` connection.

Because the Ethereum node is running inside a docker container, to connect using IPC you have to `bash` into the container first.

    docker exec -it CONTAINERNAME bash

I created a Ruby gem [elchapo](https://github.com/dilumn/elchapo) which makes everyone easy to connect to Ethereum nodes using IPC.

To connect to the Ethereum node,

    require 'elchapo'

    client = Ethereum::Connection.new("/root/.ethereum/rinkeby/geth.ipc")

You have to make sure the `.ipc` file path is correct, otherwise you will not be able to connect to Ethereum node. Inside the docker container `/root/.ethereum/rinkeby/geth.ipc` is the file path for the ipc. If you are using any other configuration find the ipc file first of all.

After you create the connection client, you can use all these Ethereum `eth` commands & call those methods.

[https://github.com/ethereum/wiki/wiki/JSON-RPC](https://github.com/ethereum/wiki/wiki/JSON-RPC)

[https://github.com/ethereum/go-ethereum/wiki/Management-APIs](https://github.com/ethereum/go-ethereum/wiki/Management-APIs)

    client.eth_accounts

Make sure you are using underscore instead of capitals. Eg: `getBalance` => `get_balance`

    client.get_balance("ACCOUNT NUMBER")


That's how you can connect to Ethereum node using IPC & execute `geth` commands in Ruby.

Cheers,

DilumN
