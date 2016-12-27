---
author: dilumnavanjana
layout: post
title: "Add Github SSH Key"
date: 2015-11-05 21:00
comments: true
category : github
tags:
- github
---

Here are the steps to configure your SSH Key with Github & communicate easily with your repositories.

# Step 1
First of all check whether you have created any public SSH keys in your computer.

{% highlight bash%}
ls -al ~/.ssh
{%endhighlight%}

Check the output you get & if you find any file named with,
`id_dsa.pub` /
`id_ecdsa.pub` /
`id_ed25519.pub` /
`id_rsa.pub`

You don't have to worry about generating the public SSH Key again. Skip the 2nd step & go to the 3rd step if you already have a public SSH Key.

---

# Step 2

To Generate public SSH Key, Copy and paste the below command to your terminal.

{% highlight bash%}
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
{%endhighlight%}
Enter your email address inside double quotation.

Make Sure that you use default settings for following option,  just press Enter to continue.

`Enter file in which to save the key (/Users/you/.ssh/id_rsa): [Press enter]`

Then enter a passphrase, just press Enter to continue.

{% highlight bash%}
Enter passphrase (empty for no passphrase): [Type a passphrase]
# Enter same passphrase again: [Type passphrase again]
{%endhighlight%}

Finally you'll be able to see the files that automatically created for public SSH Key.

---


# Step 3

Make sure that you start `ssh agent` in background by following command.

{% highlight bash%}
eval "$(ssh-agent -s)"
{%endhighlight%}

Then add the public key to `ssh agent`

{% highlight bash%}
ssh-add ~/.ssh/id_rsa
{%endhighlight%}

---


# Step 4

Finally copy the public key to clipboard by,

{% highlight bash%}
pbcopy < ~/.ssh/id_rsa.pub
{%endhighlight%}

Then go to [Github Settings SSH Page](https://github.com/settings/ssh) and add your copied SSH Key.

Cheers,
DilumN
