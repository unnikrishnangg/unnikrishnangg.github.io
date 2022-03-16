---
id: 27
title: 'Custom error code in nginx'
description: How to configure a custom error code in ngix.
date: '2016-03-04T08:07:00+00:00'
author: Unni
layout: post
guid: 'https://devopslife.io/?p=27'
permalink: /custom-error-code-in-nginx/
categories:
    - nginx
tags:
    - nginx
---

<div>In some cases, we might need to throw a custom/different error code for a specific issue. For example, we can throw a different error to the end user even if the backend node is down. We can do that in nginx as in the example below.</div><div></div><div></div>> <div>server {</div><div> listen 8080;</div><div> server_name [devopslife.io;](http://us-east-1-nginx1.posumeads.com;)</div><div> error_page 502 503 504 =204 /temperror;</div><div></div><div> location /temperror {</div><div> return 204;</div><div> }</div><div> }</div>

<div></div><div>Now the user will only see a 204 even if its 503 in real</div>