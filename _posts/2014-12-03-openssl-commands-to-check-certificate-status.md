---
id: 10
title: 'OpenSSL commands to check certificate status'
date: '2014-12-03T09:50:00+00:00'
author: Unni
layout: post
guid: 'http://devopslife.io/?p=5'
permalink: /openssl-commands-to-check-certificate-status/
categories:
    - Uncategorized
---

<div>* Check a Certificate Signing Request (CSR)</div><div></div><div>`openssl req -text -noout -verify -in CSR.csr`</div><div></div><div></div><div>* Check a private key</div><div></div><div>`openssl rsa -in privateKey.key -check`</div><div></div><div></div><div>* Check a certificate</div><div></div><div>`openssl x509 -in certificate.crt -text -noout`</div><div></div><div></div><div>* Check a PKCS#12 file (.pfx or .p12)</div><div></div><div>`openssl pkcs12 -info -in keyStore.p12`</div>