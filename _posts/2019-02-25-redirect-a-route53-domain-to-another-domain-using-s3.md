---
id: 117
title: 'Redirect a route53 domain to another domain using S3'
date: '2019-02-25T15:31:16+00:00'
author: Unni
layout: post
guid: 'https://devopslife.io/?p=117'
permalink: /redirect-a-route53-domain-to-another-domain-using-s3/
categories:
    - AWS
tags:
    - 'domain redirect in route53'
    - 'how to redirect domains in route53'
    - 'redirect domain using route53'
    - 'redirect to external domain using route53'
    - 'redirect to https using route53'
    - 'simple redirect in route53'
---

If you recently migrated your domain &amp; DNS records from some third party domain registrar to AWS Route 53, you might be searching a way to configure a simple redirect of the apex (root) domain to an external domain. Many companies used to buy all the popular TLDs of their domains to avoid cybersquatting. All of those domains will be configured with a simple redirect to the main domain. It was easy while using the domain registrar’s DNS service as we were able to configure the redirect there with ease.   
  
But, when using Route53, there is no direct way to do this. We can make use of S3 service to do this. In this example, I am trying to redirect example.org to example.com. Assuming, we already have a hosted zone for example.com.

- Create an S3 bucket with the name of domain “example.org”
- Please note that S3 bucket names must be globally unique. If the bucket name you need is already taken, you can’t use S3 for redirection and this documentation won’t be applicable for you. You may use other work arounds like redirection using a webserver in backend.
- Go to properties and select “Static web hosting”
- From the dropdown, select Redirect all requests to another host name.
- Enter example.com here and protocol (HTTP or HTTPS) and save it
- Go to Route53 and select the hosted zone for example.org
- Create a record for example.org with the below values

```
Record Type: A – IPv4 address
Alias: Yes
Alias Target: Choose your S3 bucket under the heading "S3 Website Endpoints"
Routing Policy: Simple
Evaluate Health Target: No
```

That’s it. You might need to wait for some time for the DNS propagation. Normally, the redirect will be enabled quickly. If your bucket endpoint is not populating while creating the record, Please wait for some more minutes, refresh the page and try again.