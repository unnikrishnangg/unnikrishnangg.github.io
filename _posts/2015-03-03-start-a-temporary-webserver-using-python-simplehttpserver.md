---
id: 23
title: 'Start a temporary webserver using python SimpleHTTPServer'
description: This is how we setup a simple http server using python in a single command. this is very useful to test some web content locally
date: '2015-03-03T17:03:00+00:00'
author: Unni
layout: post
guid: 'https://devopslife.io/?p=23'
permalink: /start-a-temporary-webserver-using-python-simplehttpserver/
categories:
    - Python
tags:
    - python
---

To start a HTTP server on port 8000 (which is the default port), simple type:

> python -m SimpleHTTPServer

The PWD(present working directory) by which the command is executed will be served via HTTP. If we want to use custom port, use

> python -m SimpleHTTPServer &lt;portnumber&gt;
> 
> For eg python -m SimpleHTTPServer 8080