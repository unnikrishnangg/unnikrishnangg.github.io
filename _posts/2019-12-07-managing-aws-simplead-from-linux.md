---
id: 130
title: 'Managing AWS SimpleAD from Linux'
date: '2019-12-07T16:05:25+00:00'
author: Unni
layout: post
guid: 'https://devopslife.io/?p=130'
description: 'We are checking how to manage AWS SimpleAD using a linux machine as this service is biased to Windows. There is no straightforward way to manage SimpleAD from linux when I am writing this post'
permalink: /managing-aws-simplead-from-linux/
categories:
    - aws
tags:
    - 'adcli commands'
    - 'adcli in ubuntu'
    - 'aws directory from linux'
    - 'aws simplead in linux'
    - 'change ad user password from linux'
    - 'create active directory user from linux'
    - 'create ad user from linux'
    - 'create simplead user'
    - 'simplead user management in centos'
    - 'simplead user management in linux'
    - 'simplead user management in ubuntu'
    - aws
    - simpleAD
---

SimpleAD is a managed directory service that is powered by a Samba 4 Active Directory Compatible Server. User accounts can be created in SimpleAD to access AWS applications such as AWS Client VPN, Amazon WorkSpaces, Amazon WorkDocs, or Amazon WorkMail.

I have used this service for user authentication in Client VPN. One of the challenges that we faced is that the user management in SimpleAD was very biased to Windows OS and not linux. It was not a good idea to manage a Windows server just to manage users where as all the other applications are running in Linux. After some googling, I came to know about some tools which can be used to manage users in SimpleAD. But none of them are complete or easy to understand. This inspired me to write a post on the same.

Install the packages samba-common, adcli on the Linux OS by which you are trying to manage the AD.


`apt-get install -y adcli samba-common`


Take note of the Directory domain name and the DNS servers from the AWS SimpleAD console UI. The below example assumes username is the user that we are administering, “password” is the password, vpn.example.com is the directory domain and 192.168.1.2, 192.168.1.3 as the DNS servers for the directory


```
echo "nameserver 192.168.1.2" > /etc/resolv.conf 
echo "nameserver 192.168.1.3" >> /etc/resolv.conf 
```

**Create User**

```
echo "password"|adcli create-user username --domain=vpn.example.com --display-name="User FullName" --stdin-password  
```

**Delete User**

```
echo "password"|adcli delete-user username --domain=vpn.example.com --stdin-password
```

 **List users**

```
net ads user -S vpn.example.com
```

More adcli commands can be found [here](http://manpages.ubuntu.com/manpages/cosmic/man8/adcli.8.html)