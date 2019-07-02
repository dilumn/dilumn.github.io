---
author: dilumnavanjana
layout: post
title: "Bitcoin node in Docker"
date: 2017-11-04 21:00
comments: true
category : bitcoin
tags:
- crypto
- bitcoin
---

Once I wanted to run a Bitcoin node inside a docker container. To configure a computer to run a Bitcoin is not an easy task. There are many dependencies you have to install & there are several configurations to setup. I have been going through those troubles few times & decided to move Bitcoin node into a Docker environment. So everything I have to do is build the docker image & run it.

If you want to have a look, the repository is here [bitcoin-rb](https://github.com/dilumn/bitcoin-rb).

To make things easier & clear I am going to use a `docker-compose.yml` file.

---
    version: '2'

    services:
      app:
        build: ./app
        volumes:
          - ./app:/app
        command:
          -printtoconsole
          -testnet=1
          -rest
          -rpcallowip=0.0.0.0/0
          -rpcpassword=bar
          -rpcport=18333
          -rpcuser=foo
          -server
        ports:
          - 18333:18333

---

So basically I have a directory called `app` & I include my `Dockerfile` inside that `app` folder and also I am using a volume otherwise the blocks I already synced will be gone once I stop my docker container. And there are several commands you can pass when you start the Bitcoin node.

`printtoconsole`  - Send trace/debug info to console instead of debug.log file

`testnet = 1`     - Use the test chain instead of main network

`rest`            - Accept public REST requests (default: 0)

`rpcallowip`      - Allow JSON-RPC connections from specified source. Valid for <ip> are a single IP (e.g. 1.2.3.4), a network/netmask (e.g. 1.2.3.4/255.255.255.0) or a network/CIDR (e.g. 1.2.3.4/24). This option can be specified multiple times

`rpcpassword`     - Password for JSON-RPC connections

`rpcport`         - Listen for JSON-RPC connections on <port> (default: 8332 or testnet: 18332)

`rpcuser`         - Username for JSON-RPC connections

`server`          - Accept command line and JSON-RPC commands

Here is the full list of commands you can use - [Commands](https://en.bitcoin.it/wiki/Running_Bitcoin)

---

This is the Dockerfile with everything installed

---

    FROM ubuntu:16.04

    # Install bitcoind from PPA
    RUN apt-get update
    RUN apt-get install --yes software-properties-common
    RUN add-apt-repository --yes ppa:bitcoin/bitcoin
    RUN apt-get update

    # install bitcoind (from PPA) and make
    RUN apt-get install --yes bitcoind

    # copy bitcoin.conf
    ADD . /home/bitcoind-testnet

    # WORKDIR sets the working directory for any RUN, CMD, ENTRYPOINT, COPY and ADD instructions that follow
    WORKDIR /home/bitcoind-testnet

    ENTRYPOINT ["bitcoind"]

---

This Dockerfile is installing `bitcoind` on a ubuntu image & will make the directory to run the node.

After you create the `docker-compose.yml` file & Dockerfile inside `/app` directory, you are good to run the Bitcoin node. In the root directory run,

    docker-compose build
    docker-compose -f docker-compose.yml up

That's it. You will see the Bitcoin node is starting up & start syncing the blocks.


Cheers,

DilumN
