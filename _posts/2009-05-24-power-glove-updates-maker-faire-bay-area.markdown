---
layout: post
title: Power Glove Updates, Maker Faire Bay Area
date: 2009-05-24 22:56:00 -0700
categories: diy flashbang games projects travel unity
---

Over the past few weeks I've been working on some improvements and extensions to my [Power Glove 20th Anniversary Edition]({% post_url 2009-04-03-the-power-glove-20th-anniversary-edition %}). On the tech side of things, I replaced the ugly 9V battery I was using with a low-profile, rechargeable Lithium-Polymer battery. I've updated the steps in the [Instructable](http://www.instructables.com/id/Power-Glove-20th-Anniversary-Edition/) with new pictures and instructions.

I also re-wrote my Java-Unity bridge using a UDP socket. This is a lot more elegant than the text file approach I had been using before. Now the Java program acts as a server, reading in serial data from Bluetooth and broadcasting each line as a UDP packet. The Unity input manager then reads the UDP packets and parses the actual sensor values. This should reduce disk writes, and is more reliable, so I don't have to reset the Java bridge as often. I've updated the [code bundle]({{site.baseurl}}/projects/PG20Edition/PG20Edition.zip) with the new Java and Unity source code.

The other big news is that I'm going to be exhibiting at [Maker Faire Bay Area](http://makerfaire.com/)! Maker Faire is one of my favorite gatherings -- a fantastic nexus of creative people making wonderful things. If you're in the Bay Area, you can come try the Power Glove out for yourself this weekend, May 30-31, at the San Mateo County Expo Center!

As a bonus for Maker Faire attendees, I've finished adding Power Glove support to our most popular Blurst game, [Off-Road Velociraptor Safari](http://blurst.com/raptor-safari/play)! I recorded a demo video to show it off:

<iframe src="https://player.vimeo.com/video/4821694" width="500" height="375" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>
