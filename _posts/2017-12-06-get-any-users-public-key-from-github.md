---
id: 36
title: 'Get any user&#8217;s public key from github'
description: find anyone's public key from github.
date: '2017-12-06T09:35:00+00:00'
author: Unni
layout: post
guid: 'https://devopslife.io/?p=36'
permalink: /get-any-users-public-key-from-github/
categories:
    - git
tags:
    - git
---

This is useful when you are giving SSH access to a server. Basically, we have to append the public key to ~/.ssh/authorized\_keys.

```
curl https://github.com/<username>.keys | tee -a ~/.ssh/authorized_keys
```

Replace the with real github username.