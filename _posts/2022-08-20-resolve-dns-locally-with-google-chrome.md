---
layout: post
author: Unni
title: Resolve dns locally using google chrome
date: 2022-08-20 12:40 +0800
last_modified_at: 2022-08-20T00:12:40+08:00
permalink: /resolve-dns-locally-using-google-chrome/
description: It is possible to resolve dns from google chrome itself even if we dont have admin access to update the hosts file. This comes very handy for developers who want to resolve dns locally and dont have admin access to update hosts file.
published: true
sitemap: true
categories:
    - 'windows'
    - 'google chrome'
    - 'linux'
    - 'mac'
tags:
    - 'Resolve dns entry from google chrome'
    - 'hosts override without admin access'
    - 'hosts override in google chrome'
    - '/etc/hosts in windows'
    - 'hosts override without root access'


---

It is quite easy to resolve a domain locally using the /etc/hosts file. Similar thing can be done by editing the hosts file in windows which is located at c:\Windows\System32\Drivers\etc\hosts. But this can be done only if we have Admin access. This article focus primarily on how to resolve the dns locally using google chrome browser when you are not an admin user. 

The cool part is that this doesnt even need to install any chrome extensions as well. All we need to do is to start chrome with a flag. Examples as follows. 

If you are in windows, either run the following command in run prompt (windows key + R ) or edit google chrome shortcut and append the switch there. 


```chrome.exe --host-resolver-rules="MAP devopslife.io 192.168.1.1"```

If you are on Mac, you can invoke chrome from the terminal by calling the path along with switch. This path may slightly vary depends on the version. But it isnt really hard to find. 

```/Applications/Google\ Chrome.app/Contents/MacOS/Google\ Chrome --host-resolver-rules="MAP devopslife.io 192.168.1.1"```

If we want to supply multiple rules, it can be done by appending one after another separated with a comma. 

```chrome.exe --host-resolver-rules="MAP devopslife.io 192.168.1.1, MAP devopslife.com 192.168.1.2"```



You can validate if the above switch have taken effect by going to this url. 

```chrome://version```

![](../assets/img/resolve_dns_with_google_chrome_version.png)

If it is not showing there, is is because there might be some background process running for chrome. Make sure there are no google chrome process running before we start chrome with the switch. Task manager may comes handy for you to kill the process if you are in windows. If you are in linux, then you may use pkill. 



### Checkout the references
<p><a href="https://datacadamia.com/web/browser/chrome#dns_resolver" target="_blank" rel="noopener noreferrer"> https://datacadamia.com/web/browser/chrome#dns_resolver</a></p>
