---
id: 37
title: 'Fix 404 error for permalinks while using SSL in wordpress'
date: '2018-12-15T08:11:00+00:00'
description: "fix 404 errors for permalinks while using SSL in wordpress"
author: Unni
layout: post
guid: 'https://devopslife.io/?p=37'
redirect_from:
    - /tag/wordpress-5-permalinks-issue/
permalink: /fix-404-error-for-permalinks-while-using-ssl-in-wordpress/
categories:
    - wordpress
tags:
    - '404 error wordpress'
    - '404 error wordpress permlinks'
    - 'Fix 404 error for permalinks while using SSL in wordpress'
    - 'fix 404 error wordpress'
    - 'letsencrypt ssl wordpress 404'
    - 'permalinks in wordpress'
    - 'wordpress 5 permalinks issue'
    - 'wordpress giving 404 for permalinks'
    - 'wordpress permalinks not working'
    - wordpress
---

This was an issue I have faced while setting up this blog. I was getting 404 errors for all the post links in this blog when selecting the non default permalink structure with SSL.

First thing I tried was to regenerate the .htaccess file. Removed the existing .htaccess file in the WordPress root folder. Regenerated the file by switching the permalink again. That didnt work for me. The fix was something with the web sever level. Finally, I found the fix.

The directory tag is required in <g class="gr_ gr_4 gr-alert gr_spell gr_inline_cards gr_run_anim ContextualSpelling ins-del multiReplace" data-gr-id="4" id="4">ssl</g> virtual host config of apache same as of <g class="gr_ gr_5 gr-alert gr_spell gr_inline_cards gr_run_anim ContextualSpelling ins-del multiReplace" data-gr-id="5" id="5">http</g> port 80, to allow <g class="gr_ gr_7 gr-alert gr_spell gr_inline_cards gr_run_anim ContextualSpelling ins-del multiReplace" data-gr-id="7" id="7">override redirect</g> rules using .htaccess of <g class="gr_ gr_6 gr-alert gr_spell gr_inline_cards gr_disable_anim_appear ContextualSpelling ins-del multiReplace" data-gr-id="6" id="6">wordpress</g>.

Example


```
<virtualhost>
    <Directory /var/www/html/devopslife.io/>
        DirectoryIndex index.php
        AllowOverride All
        Order allow,deny
        Allow from all
    </Directory>
</VirtualHost></virtualhost>
```


Thanks to this [digitalocean thread ](https://www.digitalocean.com/community/questions/wordpress-permalinks-404-under-ssl)