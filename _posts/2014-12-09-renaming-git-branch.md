---
id: 18
title: 'Renaming git branch'
description: Renaming a git branch.
date: '2014-12-09T16:22:00+00:00'
author: Unni
layout: post
guid: 'https://devopslife.io/?p=18'
permalink: /renaming-git-branch/
categories:
    - git
tags:
    - git
---

<div>1. Rename your local branch.</div><div></div><div>If you are on the branch you want to rename:</div><div></div>> <div>git branch -m new-name</div>

<div></div><div>2. Delete the old-name remote branch and push the new-name local branch.</div><div></div>> <div>git push origin :old-name new-name</div>

<div></div><div>3. Reset the upstream branch for the new-name local branch. Switch to the branch and then:</div><div></div>> <div>git push origin -u new-name</div>