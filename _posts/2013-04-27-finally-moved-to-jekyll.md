---
layout: post
title: "finally moved to jekyll"
description: "guide to move from wordpress to jekyll"
repo: dcalderon.github.com
category: tutorials
tags: [jekyll, help, wordpress, static, blog]
image: 
---
{% include JB/setup %}
<!-- Photos will be in /assets/images/2013-04-27-finally-moved-to-jekyll/ -->
<!-- <img id="aboutPhoto" src="/assets/images/2013-04-27-finally-moved-to-jekyll"/> -->
<!-- Template for youtube video embed -->
<!-- <object class="youtube" type="application/x-shockwave-flash" data="http://www.youtube.com/v/VID_ID&amp;hl=en&amp;fs=1&amp;rel=0" width="560" height="315"><param name="movie" value="http://www.youtube.com/v/VID_ID&amp;hl=en&amp;fs=1&amp;rel=0" /><param name="allowFullScreen" value="true" /></object> -->
<!-- Link reference for my old brain -->
<!-- <a href="" target="_blank"></a> -->

### As the title says,

I finally ditched the wordpress and moved on to static pastures. Wordpress provides a hassle free CMS that even your grandma can use, but quickly becomes bloated. Almost counterintuitively, switching blogging frameworks was a more involved process than I expected when I began tinkering with various blog platforms. 

Migrating can be tough. There are those who like to control every aspect of their final product and will most likely spend a lot of time on minor tweaks. Others are looking for the quick fixes. Use these details as a guideline so you can be as thorough as you'd like to be.

### Familiarize yourself with <a href="http://jekyllbootstrap.com/lessons/jekyll-introduction.html" target="_blank">Jekyll</a>

My first obstacle to getting off of Wordpress was trying to find an alternative. I wanted something easy, and fast. Lots of blogs I liked used static solutions so I figured I'd give one a try. After a few google searches I found <a href="http://jekyllrb.com/" target="_blank">jekyll</a>. It seemed to be everything I was looking for and had a solid supporting open-source community. Plus learning jekyll would give me the chance to look at some ruby code (I've dealt mainly with python in the past).

Since I don't consider myself particularly skilled at html/css design I began looking through jekyll blogs for inspiration and clues into how I could make my own site. I found <a href="http://jekyllbootstrap.com/" target = "_blank">jekyll-bootstrap</a> (JB), which as the name implies is a merger between the static site converter and the popular front end twitter framework. For the beginner, I strongly suggest working through the <a href="http://jekyllbootstrap.com/usage/jekyll-quick-start.html" target="_blank">tutorial</a> to understand important aspects of running a jekyll site like markdown, liquid converters, yaml, etc.

### Build a site

Another neat feature of jekyll-bootstrap is the ability to work with themes. Rake provides simple download and installation

    $ rake theme:install name="theme-the-minimum"
functionality. Above we have a script to install a theme called "the-minimum" which should be placed in the **./\_theme\_packages** directory, and which is what I used as a starting point.

After looking through and documenting all my favorite aspects of JB on <a href="https://github.com/mojombo/jekyll/wiki/Sites" target="_blank">open sourced sites</a>, I began the long process of building my frankenstein personal site. No one can really teach this part. In my case, I just tinkered until I found something I liked. Some online tools I found useful were <a href="http://subtlepatterns.com/" target="_blank">this</a> site for amazing patterns and <a href="http://www.colorhexa.com/" target="_blank">here</a> for color reference.

For more detailed info on my development process I suggest you star and follow the <a href="https://github.com/dcalderon/dcalderon.github.com" target="_blank">source code</a>. Feel free to ask me any questions. 

### Host for free!

This is the real sweet part of the deal when you jump into running a static site. Finding free hosting is easy. My page is hosted at no cost using <a href="http://pages.github.com/" target="_blank">GitHub Pages</a> (the downside is that you'll have to make do without jekyll plugins for security reasons). In my case I had a custom domain that I wanted to point to my github pages. To do this simply,

1. create a repository named USERNAME.github.com, with your username switched in, 
2. create a file in your root static site directory called CNAME with the custom domain name you own,
3. push up the static site to your newly created repository, 
4. be sure to have two branches one entitled master and the other gh-pages (github can get a little touchy here, but at this point your site should be available at username.github.com),
5. on your domain provider create an "A Record" from your domain that points to GitHub's IP address (204.232.175.78),
6. be a little patient.

Once the DNS lookups update if you go to your domain it should point to your github-hosted personal site. Some of these steps can become a little muddled but there is decent documentation available online. I know <a href="bitbucket.org" target="_blank">bitbucket</a> also has a similar service. For the few days I've been experimenting I am totally happy with github pages. Godaddy never served anything so quickly.


### Save all the old content \[Optional\]

While I was busy jumping ship, nostalgia kicked in. I wasn't ready to simply ditch all the hard work I put into telling my silly stories while studying abroad. Yet, I was serious when I said static is the way to go. To solve this problem I decided to export my Wordpress site into a static format and host it as well on <a href="https://github.com/dcalderon/abroad" target="_blank">github pages</a>. Looking for an exporter was a bit tricky, but in the end I tweaked a little <a href="http://www.linuxjournal.com/content/downloading-entire-web-site-wget" target="_blank">wget script</a> for my purposes:

	wget 
	  \ --recursive
	  \ --no-clobber
	  \ --page-requisites
	  \ --html-extension
	  \ --convert-links
	  \ --restrict-file-names=unix
	  \ --domains diegocalderon.info
	  \ --no-parent
	  \ http://diegocalderon.info/travels/
The tutorial gives a nice description of each parameter. Within 20 minutes my whole site was scraped. Cool. Then I followed the steps from the previous section (except for the domain provider tweaks) and updated my static site to link to it. <a href="https://www.google.com/search?q=viola&amp;aq=f&amp;um=1&amp;ie=UTF-8&amp;hl=en&amp;tbm=isch&amp;source=og&amp;sa=N&amp;tab=wi&amp;ei=Tqh8UdSIEIe60AHZl4GIAQ&amp;biw=1099&amp;bih=715&amp;sei=UKh8UebmCqa30AG7oIHYBw" target="_blank">Voila!</a>

### Proudly display

Throughout my process I tried to acknowledge people who inspired me. If you enjoyed this tutorial or it helped get you out of a rut please feel free to let me know. Also, comment if you have any difficulties and I'll be happy to share my experiences. Finally once you have your own polished product add it to the list and gleam with pride!

<a href="http://imgur.com/FmteYxL" title=""><img src="http://i.imgur.com/FmteYxL.jpg" title="Dr. Jekyll and Mr. Wordpress" alt="Dr.Jekyll and Mr. Wordpress" /></a>