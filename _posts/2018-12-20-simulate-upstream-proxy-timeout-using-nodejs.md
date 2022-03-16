---
id: 51
title: 'Simulate upstream proxy timeout using nodejs'
description: "Simulate nginx upstream timeout using nodejs. this is useful when we want to simulate slowness in upstream without making it completely down"
date: '2018-12-20T16:20:07+00:00'
author: Unni
layout: post
redirect_from:
    - /tag/simulate-upstream-proxy-timeot/
guid: 'https://devopslife.io/?p=51'
permalink: /simulate-upstream-proxy-timeout-using-nodejs/
categories:
    - nodeJS
tags:
    - 'how to test proxy_read_timeout'
    - nginx
    - nodejs
    - 'Simulate upstream proxy timeot'
    - 'Simulate upstream proxy timeout using nodejs'
    - upstream_proxy_timeout
    - nodeJS
---

This is something that I have came across while tuning an nginx server which has multiple tomcat instances as upstream. We were trying to adjust the read timeout of the upstream proxies. It is hard to simulate this by stopping the backend as it will throw a 503 bad gateway. So, for simulating this, we used a nodejs script.

```

/*server.js*/
const http = require('http');
const hostname = '0.0.0.0';
const port = 8080;
function test(res) {
console.log("Inside test");
}
const server = http.createServer(function(req, res) {
console.log("Starting");
setTimeout(test, 20000);
});

server.listen(port, hostname, function() {
console.log('Server running at http://'+ hostname + ':' + port + '/');
});

```