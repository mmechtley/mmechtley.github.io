---
layout: post
title: Make the Future You Imagined – The Power Glove – 20th Anniversary Edition
date: 2009-04-03 10:20:00 -0700
categories: diy flashbang games hacks projects unity
---

I always loved the Nintendo Power Glove. Not because it was a fun or useful peripheral -- it wasn't. In fact it wasn't bad, as [Lucas](http://www.imdb.com/title/tt0098663/quotes) asserted, it was absolutely terrible. Only two games were ever made to work with it -- Super Glove Ball and Bad Street Brawler. You could use it with other NES games of course, but it was just an obfuscated controller. Plus, it was horribly imprecise, and since it required a sensor bar to find its orientation, you had to hold your hand at shoulder level all the time. No, I loved the Power Glove for what it represented -- a precursor to virtual reality, a way for humans to directly manipulate computers, like an artifact from some sort of alternate future Earth.

I realized one day that we're actually living in that future. It doesn't look the same as we imagined it, but the necessary elements are all there. It's been 20 years now since Mattel released the Power Glove, in 1989. Especially in the last few years, the availability of sophisticated sensing equipment to hardware hackers has grown by leaps and bounds. Technology like programmable microcontrollers, accelerometers, and Bluetooth are readily available -- and cheap. In short, the time is ripe to re-make the Power Glove -- and make it _right_.

Over the past month, I've done just that. I stripped the guts out of an original Power Glove, replaced the ultrasonic sensors with an accelerometer, the proprietary microcontroller with an open-source Arduino, and the wired connection with Bluetooth. I wrote an input manager to get the data into [Unity](http://unity3d.com), and hooked it up to the boxing game Adam and I are making for iPhone, Touch KO. What's more, I've documented the whole process so that you can make you own!

<iframe src="https://player.vimeo.com/video/3985361" width="500" height="375" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>

I have a video, photos, and an instructable of the build process, and have the schematic, Arduino, and Unity code available for download. You can read the data in any way you like, but since many software packages don't have direct access to serial ports (Unity included), I've also written a small Java program that takes the input and dumps it directly to a text file.

Side note: Since my last post I tried and now totally dig twitter. [Follow me](http://twitter.com/biphenyl).

- [Instructable](http://www.instructables.com/id/Power-Glove-20th-Anniversary-Edition/")
- [Video on Vimeo](http://vimeo.com/3985361)
- [Build Photoset on Flickr](http://www.flickr.com/photos/mmechtley/sets/72157615867731266/)
- [Circuit Schematic]({{site.baseurl}}/projects/PG20Edition/PG20EditionSchematic.pdf)
- [Zip of Arduino, Unity, and Java code]({{site.baseurl}}/projects/PG20Edition/PG20Edition.zip)
