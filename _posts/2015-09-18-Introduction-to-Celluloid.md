---
author: dilumnavanjana
layout: post
title: "Introduction to Celluloid"
date: 2015-09-18 21:00
comments: true
category : celluloid
tags:
- celluloid
---

Celluloid provides a simple and natural way to build fault-tolerant concurrent programs in Ruby. With Celluloid, you can build systems out of concurrent objects just as easily as you build sequential programs out of regular objects. Recommended for any developer, including novices, Celluloid should help ease your worries about building multithreaded Ruby programs.
By combining concurrency with object oriented programming, Celluloid frees you up from worry about where to use threads and locks. Celluloid combines them together into a single concurrent object oriented programming model, encapsulating state in concurrent objects and thus avoiding many of the problems associated with multithreaded programming. Celluloid provides many
features which make concurrent programming simple, easy, and fun:

# Automatic "deadlock-free" synchronization:
Celluloid uses a concurrent object model which combines method dispatch and thread synchronization. Each actor is a concurrent object running in its own thread, and every method invocation is wrapped in a fiber that can be suspended whenever it calls
out to other actors, and resumed when the response is available. This means methods which are waiting for responses from other actors, external messages, or other system events (including I/O with Celluloid::IO) can be suspended and will never block other methods that are ready to run. This won't prevent bugs in Celluloid, bugs in other thread-safe libraries you use, and even certain "dangerous" features of Celluloid from causing your program to deadlock, but in general, programs built with Celluloid will be naturally immune to deadlocks.

# Fault-tolerance:
Celluloid has taken to heart many of Erlang's ideas about fault-tolerance in order to enable self-healing applications. The central idea: have you tried turning it off and on again? Celluloid takes care of rebooting subcomponents of your application when they crash, whether it's a single actor, or large (potentially multi-tiered) groups of actors that are all interdependent. This means rather than worrying about rescuing every last exception, you can just sit back, relax, and let parts of your program crash, knowing Celluloid will automatically reboot them in a clean state. Celluloid provides its own implementation of the core fault-tolerance concepts in Erlang including linking,supervisors,and supervision groups.

# Futures:
Ever wanted to call a method "in the background" and retrieve the value it returns later? Celluloid futures do just that. It's like calling ahead to a restaurant to place an order, so they can work on preparing your food while you're on your way to pick it up. When you ask for a method's return value, it's returned immediately if the method has already completed, or otherwise the current method is suspended until the value becomes available.

Cheers,
BC_Dilum
