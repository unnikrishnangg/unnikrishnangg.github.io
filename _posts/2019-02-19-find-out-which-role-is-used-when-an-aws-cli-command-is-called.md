---
id: 102
title: 'Find out which role is used when an AWS CLI command is called'
date: '2019-02-19T11:11:28+00:00'
author: Unni
layout: post
guid: 'https://devopslife.io/?p=102'
permalink: /find-out-which-role-is-used-when-an-aws-cli-command-is-called/
categories:
    - AWS
tags:
    - 'find iam role'
    - 'find iam role of aws cli'
    - 'find iam role of aws cli commands'
    - 'find instance profile of aws cli'
    - 'find out iam role'
    - 'Find out which role is used when an AWS CLI command is called'
---

This is very useful if you are running an AWS command on an ec2 instance which is using an IAM role or instance profile and you would like to verify if it is using the intended role.

[aws sts get-caller-identity](https://docs.aws.amazon.com/cli/latest/reference/sts/get-caller-identity.html)

```
$ aws sts get-caller-identity
{
    "Account": "0123456789",
    "UserId": "ABCDxxx:i-abc123",
    "Arn": "arn:aws:sts::0123456789:assumed-role/ECS_Opsworks_DefaultRole/i-abc123"
}
```