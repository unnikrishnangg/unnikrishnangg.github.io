---
layout: post
author: Unni
title: Migrating the wordpress blog to jekyll in github pages
date: 2022-03-19 10:07 +0800
last_modified_at: 022-03-19 10:07 +0800
permalink: /migrating-wordpress-to-github-pages/
description: this post is a highlever explanation on how to migrate your wordpress blog to jekyll to host it free on github pages.
published: true
sitemap: true
categories:
    - 'Wordpress'
    - 'Jekyll'
    - 'Github pages'
tags:
    - 'migrate wordpress to github pages'
    - 'migrate wordpress to jekyll'
    - 'hosting in github pages'


---

I was not getting much time recently to maintain this blog. We all know how dangerous it is to keep something in internet unmaintained amidst the new vulnerabilities which are coming up day by day. The same applies to wordpress as it have multiple third party plugins as well which may open doors to hackers unless we update it with all patches. I read an article in Linkedin recently about jekyll which is a static site generator based on ruby. The good thing about jekyll is it can be hosted in github pages for free. 


This is not a detailed step by step guide. But I am trying to cover the process in a high level. 

I have used a wordpress plugin "Jekyll Exporter" to migrate the wordpress posts to the jekyll specific format. Installing the plugin will give an option to "export to jekyll" in the tools menu. 

![](/assets/img/jekyll_exporter_in_wordpress.png)

But it was not working for me due to some reason. but there was another way using the wp cli which helped me to achieve this. Try this way if you are also facing the issue to export it using wp admin portal.

```wp jekyll-export > export.zip```

The zip file contains a folder structure which we will use later. 


1. Create a github repo with the naming convention your-github-username.github.io
2. Clone this repo to your local
3. gem install  bundler jekyll
4. jekyll new your-github-username.github.io


replace the content of our cloned git with the directory we just created using step above. 

This way we created a basic jekyll website. If you want to see how it looks like locally, we can use this command

```bundle exec jekyll serve```

If you are using Ruby version 3.0.0 or higher, above command may fail. This can be fixed by adding webrick to your dependencies: 

```bundle add webrick```

If it complains for any gems, just install it using gem install command. 

compare the ```_config``` file in the backup and newly created folders and correct fields accordinly. It is somewhat similar to the wp-config.php file. If we are adding any new gems , we have to add it to the Gemfile as well. 

Now, we can just swap the ```_posts``` folder in the newly created jekyll folder with the one from the export we got from wordpress and we are done. 

### Challenges and workarounds
1. The wordpress theme will not be same and so the blog may look different. 

	--> You can playaround using the main.css or find a similar jekyll theme to make it look similar. Check the respective jekyll theme documentation to find the customizations and css path. Either add the theme to your repo or use a remote_theme. More details on all these are available in the official documentation. 

2. Broken permalinks which can impact SEO score. 
	--> htaccess is not supported in github pages but we can do meta refresh. I found the jekyll plugin "jekyll-redirect-from" very useful to deal this. 

    --> Use jekyll-sitemap plugin for creating a sitemap.Have a look at jekyll-seo-tag plugin as well. 

 3. ruby gem dependencies. 
 	--> this is where I spend lot of my time setting this up. Make sure to install the required ruby gems and add that to the Gemfile. 

### More customizations
1. Possible to add a custom domain name in the github settings. 
2. Try different themes available in the github settings itself and the external ones.
3. Lots of plugins are also available for jekyll however dont expect it as vast as wordpress plugins. 


### Checkout the references
<p><a href="https://jekyllrb.com/docs/" target="_blank" rel="noopener noreferrer"> https://jekyllrb.com/docs/</a></p>
<p><a href="https://wordpress.org/plugins/jekyll-exporter/" target="_blank" rel="noopener noreferrer">https://wordpress.org/plugins/jekyll-exporter/</a>.</p>
<p><a href="https://www.bawbgale.com/from-wordpress-to-jekyll/" target="_blank" rel="noopener noreferrer">https://www.bawbgale.com/from-wordpress-to-jekyll/</a></p>


