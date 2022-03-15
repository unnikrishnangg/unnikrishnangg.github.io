---
id: 21
title: 'Remove a commit from local and remote history'
date: '2015-01-03T16:24:00+00:00'
author: Unni
layout: post
guid: 'https://devopslife.io/?p=21'
permalink: /remove-a-commit-from-local-and-remote-history/
categories:
    - Uncategorized
---

> - git reset –soft commit\_id
> - git stash save “message”
> - git reset –hard commit\_id
> - git stash apply stash stash@{0}
> - git push —force