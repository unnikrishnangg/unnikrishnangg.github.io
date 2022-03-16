---
id: 11
title: 'Delete a git commit that is already pushed'
description: "delete a git commit that is already pushed"
date: '2014-12-07T09:54:00+00:00'
author: Unni
layout: post
guid: 'https://devopslife.io/?p=8'
permalink: /delete-a-git-commit-that-is-already-pushed/
categories:
    - git
tags:
    - git
---

<div>> <div>git log</div>

</div><div> to check the commit list.</div><div></div><div>For example, commit 7f6d03 was before the 2 wrongful commits and we want to restore to that commit .</div><div></div><div>Force push that commit as the new master:</div><div></div><div>> <div>git push origin +7f6d03:master</div>

</div><div></div><div>The + is interpreted as forced push.</div><div></div><div></div><div>Another way</div><div></div><div>You can also use git reset to undo things. Then force push.</div><div></div><div>> <div>git reset 7f6d03 –hard</div><div>git push origin -f</div>

</div>