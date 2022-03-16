---
id: 10
title: 'OpenSSL commands to check certificate status'
description: the essential commands to play with ssl certificate and keys. This will be useful to inspect an ssl certificate or CSR.
date: '2014-12-03T09:50:00+00:00'
author: Unni
layout: post
guid: 'http://devopslife.io/?p=5'
permalink: /openssl-commands-to-check-certificate-status/
categories:
    - openssl
tags: 
    - openssl
---

* Check a Certificate Signing Request (CSR) <br> 
`openssl req -text -noout -verify -in CSR.csr` <br> 

* Check a private key <br> 
`openssl rsa -in privateKey.key -check`
<br> 

* Check a certificate <br> 
`openssl x509 -in certificate.crt -text -noout`<br> 

* Check a PKCS#12 file (.pfx or .p12)<br>
`openssl pkcs12 -info -in keyStore.p12`