---
id: 127
title: 'Testing cloudwatch alarm using AWS CLI'
date: '2019-06-07T07:22:00+00:00'
author: Unni
layout: post
guid: 'https://devopslife.io/?p=127'
permalink: /testing-cloudwatch-alarm-using-aws-cli/
categories:
    - CLI
    - Cloudwatch
tags:
    - aws cli test cloudwatch
    - aws
    - change cloudwatch alarm state
    - simulate cloudwatch alarm
    - simulate cloudwatch alarms
    - test cloudwatch
    - test cloudwatch alarm
    - testing cloudwatch alarm
    - trigger cloudwatch alarm manuallu
    - trigger cloudwatch alarm manually
---

Many of us are using Cloudwatch alarms for triggering some action. It could be an SNS or a lambda function etc. We can use this AWS CLI command to temporarily set cloudwatch alarm state for testing purposes.

We can change the state of the alarm “MyalarmName” to ALARM as follows.

```yml
aws cloudwatch set-alarm-state –alarm-name MyalarmName –state-reason “testing alarm” –state-value ALARM
```


The alarm returns to actual state usually within seconds.