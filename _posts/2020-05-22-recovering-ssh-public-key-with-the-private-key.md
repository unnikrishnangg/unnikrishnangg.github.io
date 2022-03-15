---
id: 135
title: 'Recovering SSH public key with the private key'
date: '2020-05-22T05:24:25+00:00'
author: Unni
layout: post
guid: 'https://devopslife.io/?p=135'
permalink: /recovering-ssh-public-key-with-the-private-key/
categories:
    - Linux
tags:
    - 'find deleted public key'
    - 'find public key with private'
    - 'is it possible to recover public key ssh'
    - 'lost public key'
    - 'lost publickey'
    - 'recover public key with private key'
    - 'Recovering SSH public key with the private key'
    - 'ssh passwordless authentication'
    - ssh-keygen
---

I recently came across this situation by which the public SSH key of a server is lost and I was instructed to add the public key to other server’s authorized\_hosts file to enable password less SSH authentication. However I was not allowed to create a new keypair as the old key could be in place in multiple places. This ssh-keygen command was a lifesaver.

This command will recover the public key if you have the private key with you.

`ssh-keygen -y -f id_rsa_private_key_file > publickey.pub`

Please let me know via comments if you are having trouble with this command.