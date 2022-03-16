---
id: 91
title: 'Using profiles in Boto3'
date: '2019-02-15T19:09:15+00:00'
author: Unni
layout: post
guid: 'https://devopslife.io/?p=91'
permalink: /using-profiles-in-boto3/
description: "using aws profiles in boto3. this is useful if you have defined multiple aws profiles in your shell "
categories:
    - AWS
    - python
tags:
    - 'aws boto3'
    - 'how to switch profile in boto3'
    - 'login to different aws accounts in boto3'
    - 'switch profile in boto3'
    - 'switch role in boto3'
    - 'using boto3 with aws iam'
    - python
    - aws
---

If you are a boto3 user and have multiple AWS profiles defined in your shell, I am sure that you have faced this issue at least once. Boto3 loads the default profile if you don’t specify explicitly. I am trying to explain how to specify AWS profiles while using boto3.

Lets say, we want to use the profile “dev”, We have the following ways in boto3.

####  1. Create a new session with the profile

```
dev = boto3.session.Session(profile_name='dev')
```


#### 2. Change the profile of the default session in code

```
boto3.setup_default_session(profile_name='dev')
```


####  3. Change the profile of the default session with an environment variable

```
$ AWS_PROFILE=dev python
```

We can also list the available profiles defined in our configuration

```
boto3.session.Session().available_profiles
```


Reference : <https://stackoverflow.com/questions/33378422/how-to-choose-an-aws-profile-when-using-boto3-to-connect-to-cloudfront>