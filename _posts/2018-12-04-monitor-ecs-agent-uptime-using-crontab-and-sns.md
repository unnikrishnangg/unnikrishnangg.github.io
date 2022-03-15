---
id: 31
title: 'Monitor ECS agent uptime using crontab and SNS'
date: '2018-12-04T08:29:00+00:00'
author: Unni
layout: post
guid: 'https://devopslife.io/?p=31'
permalink: /monitor-ecs-agent-uptime-using-crontab-and-sns/
categories:
    - Uncategorized
tags:
    - 'aws ecs agent'
    - 'ecs agent'
    - 'ecs monitoring'
    - 'how to monitor ecs'
    - 'monitor ecs'
    - 'monitor ecs agent'
    - 'Monitor ECS agent uptime using crontab and SNS'
    - 'monitor ecs container'
---

<div>The Amazon ECS container agent allows container instances to connect to your cluster. If this agent is down for some reason, deployments to the service won’t be reflected in the instance and can cause discrepancy.</div><div></div><div>Here is a one-liner to check if ECS agent container is running. If it is not running, we are making use of AWS SNS service to send a notification to a topic.</div><div></div><div></div>> <div>if [ -z $(docker ps -f “name=ecs-agent” -f “status=running” -q) ]; then /usr/bin/aws –region=us-east-1 sns publish –topic-arn “arn:aws:sns:us-east-1:123456789012:Topicname” –message “ECS Agent is not running in $HOSTNAME.”; fi</div>

<div></div><div></div><div>Make sure that the instance role has permissions to publish to the required topic and the topic is already configured.</div>