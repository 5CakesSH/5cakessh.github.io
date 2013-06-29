---
layout: post
title: "konami code win"
description: "Add a konami easter egg to your site!"
repo: 
category: tutorials
tags: [help, howto, javascript]
head: do it!

---
{% include JB/setup %}
<!-- Photos will be in /assets/images/2013-05-02-konami-code-win/ -->
<!-- <img id="aboutPhoto" src="/assets/images/2013-05-02-konami-code-win"/> -->
<!-- Template for youtube video embed -->
<!-- <object class="video" type="application/x-shockwave-flash" data="http://www.youtube.com/v/VID_ID&amp;hl=en&amp;fs=1&amp;rel=0" width="560" height="315"><param name="movie" value="http://www.youtube.com/v/VID_ID&amp;hl=en&amp;fs=1&amp;rel=0" /><param name="allowFullScreen" value="true" /></object> -->
<!-- Link reference for my old brain -->
<!-- <a href="" target="_blank"></a> -->

### Recently,
I was given the task of getting a previously written RoR app up and running. Since I had no part in its development I wanted to contribute something small to mark my legacy. It's already a beautifully simple app, thus adding anything to the basic interface would likely be ungainly. Instead, it would be fun to leave my mark in the form of an <a href="http://en.wikipedia.org/wiki/Easter_egg_(media)" target="_blank">easter egg</a>, and everyone knows the most famous easter egg out there, the konami code!!


### Javascript to the rescue!
Without searching I knew someone must have implemented it all in a javascript library (<a href="http://harthur.github.io/kittydar/" target="_blank">seriously there are some neaaat code projects</a>). Just as I suspected I found <a href="http://snaptortoise.com/konami-js/" target="_blank">konami-js</a>. Not that it would be too difficult to implement things yourself, I think it's also a good practice to be familiar with libraries available and try them out.

Simply add this

    <script type="text/javascript"
    src="https://raw.github.com/snaptortoise/konami-js/master/konami.js"></script>
    <script type="text/javascript">
	var success = function() {
		alert("You have entered the KONAMI CODE!  You now have 30 lives.  Kinda.")
	}
	var konami = new Konami(success);
    </script>

into your site's HTML (I usually put it in between the head tags). And there you go, an alert should pop up when you type Up, Up, Down, Down, Left, Right, Left, Right, B, A, Start (replaced with Enter).

Better yet the guys at snaptortoise define a *konami.pattern* variable to store whatever key stroke pattern you are looking for triggering any exciting thing your heart desires.

	<script type="text/javascript" src="https://raw.github.com/snaptortoise/konami-js/master/konami.js"></script>
	<script type="text/javascript">
	var success = function() {
		alert("You have hit up four times.  Why you did this, I don't know.")
	}
	konami = new Konami(success)
	konami.pattern = "383838383838383838383838"
	</script>
	
I suggest using some sort of KeyCode <a href="http://www.cambiaresearch.com/articles/15/javascript-char-codes-key-codes" target="_blank">reference</a> and you are off to the races. Oh and you wonder how to set up the konami code for mobile? Lucky you it is already included! That's right simply replace B, A, Start with three direct taps.

### Try it out

The best way to come up with cool ideas is to do it yourself and have fun. Of course this blog post would have konami code easter egg functionality! However, now see what happens if you go to my homepage (or anywhere on my blog) and type my name.

<img id="hiddenVid" src="/assets/images/2013-05-02-konami-code-win/konami-code-blog.jpg"/>

\[EDIT\] Someone sent me [this](http://easteregg.in/) great site for many more easter egg ideas!


