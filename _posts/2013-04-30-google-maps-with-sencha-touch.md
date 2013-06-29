---
layout: post
title: "Google maps with Sencha Touch"
description: "A short tutorial on how to add a google map to your sencha touch app."
repo: WesInfo
category: tutorials
tags: [sencha, help, mobile, howto]
image: 
---
{% include JB/setup %}
<!-- Photos will be in /assets/images/2013-04-30-google-maps-with-sencha-touch-2/ -->
<!-- <img id="aboutPhoto" src="/assets/images/2013-04-30-google-maps-with-sencha-touch-2"/> -->
<!-- Template for youtube video embed -->
<!-- <object class="video" type="application/x-shockwave-flash" data="http://www.youtube.com/v/VID_ID&amp;hl=en&amp;fs=1&amp;rel=0" width="560" height="315"><param name="movie" value="http://www.youtube.com/v/VID_ID&amp;hl=en&amp;fs=1&amp;rel=0" /><param name="allowFullScreen" value="true" /></object> -->
<!-- Link reference for my old brain -->
<!-- <a href="" target="_blank"></a> -->

### Sencha is cool

If you haven't heard mobile apps are pretty cool. Even your mother has an app idea she tried to sell to you. The first step towards achieving mobile app success is picking a platform. Do you go with the traditional App Store and Objective-C or shoot for the masses with Java and Android?

As part of a group designing small apps for our University we chose to access the best of both worlds with Sencha Touch. Sencha provides a user interface Javascript library specifically designed for the mobile web. The plan is to code a web app in javascript and HTML then cross-compile for various target platforms. I have yet to actually cross compile myself, so am somewhat skeptical of Sencha's viability, but the allure of cross-compatibility is irresistible.

### Maps are helpful

We are planning to add a map view to our app. Maps are common features in mobile apps, which add a spatial component that helps connect the user with their environment. I thought it would be a difficult task but was quickly proven wrong. All you have to do is add

    <script type="text/javascript" src="http://maps.google.com/maps/api/js?sensor=true"></script>

to your *index.html* file in the app's root directory to load the google maps API. Then add,

    Ext.Viewport.add({
    xtype: 'map',
    useCurrentLocation: true
	});
	
within your app, and a full-fledged map should appear centered on your current location.

### Profit!

Now that your app has a map and access to the google api, there are no limits to what you can make! Next step profit! Their <a href ="http://docs.sencha.com/touch/2.2.0/#!/api/Ext.Map" target="_blank">documentation</a> sometimes is a bit confusing, so don't get discouraged.

<img src="/assets/images/2013-04-30-google-maps-with-sencha-touch-2/map.png"/>

