---
layout: post
title: Drunkpong – an Excuse to Make a USB Breathalyzer
date: 2008-02-19 02:13:00 -0700
categories: diy games hacks projects
---

You're throwing a party for the [Game Developers Conference](http://gdconf.com/) and you think it would be cool to have a custom game. What's the natural response? How about Pong that adapts its difficulty based on how drunk you are!

Among my numerous interests is custom hardware for games and interactive art. When my friend and coworker [Matthew Wegner](http://fun-motion.com/) suggested the idea of making a breathalyzer peripheral for a party game at GDC, how could I respond with anything but, "Hahahaha, Hells YES! I am ON that!"

I started by researching the various consumer breathalyzers. In the end I decided to hack the [Alcoscan AL2500](http://alcomate.net/alcoscan-al2500.html). It provides readings within a reasonable error tolerance and costs about $30 on Amazon -- much cheaper than fuel cell meters. Upon opening it up, I found that it's set up pretty simply. It's driven by an ATMEGA48V-10AU microcontroller, with the semiconductor sensor connected to an analog input, and digital outputs that drive a simple seven-segment style LCD.

{% include figure.html url="http://farm3.static.flickr.com/2313/2276954688_b21841e347_m.jpg" alt="Alcoscan AL2500 Breathalyzer" caption="Alcoscan AL2500 Breathalyzer" link="http://www.flickr.com/photos/mmechtley/2276954688/" class="image-packed" %}

{% include figure.html url="http://farm3.static.flickr.com/2341/2276957674_ee1d6cd7f9_m.jpg" alt="Board, back. Simple AVR microcontroller with sensor as an analog input and LCD as digital outputs" caption="Board, back. Simple AVR microcontroller with sensor as an analog input and LCD as digital outputs" link="http://www.flickr.com/photos/mmechtley/2276957674/" class="image-packed" %}

As I saw it, there were basically two options for obtaining the data from the breathalyzer and sending it to the computer. On the one hand, you could read the analog value from the breath sensor, or on the other hand, you could reconstruct the LCD digits from the digital outputs. Since the analog circuit driving the sensor was a little complicated and beyond my expertise (and I'd procrastinated enough that learning more before GDC was out of the question), I decided to reconstruct digits. I first followed traces on the PCB to find which pins on the microcontroller were driving the LCD. I then systematically grounded each pin while turning the unit on to determine which pins drove which LCD segments.

{% include figure.html url="http://farm3.static.flickr.com/2339/2276170061_720ddc3156_m.jpg" alt="Mapping out which pins control which LCD segments" caption="Mapping out which pins control which LCD segments" link="http://www.flickr.com/photos/mmechtley/2276170061/" class="image-packed" %}

{% include figure.html url="http://farm3.static.flickr.com/2335/2276172743_4f1a68fe09_m.jpg" alt="Pin cross reference for AVR microcontroller and LCD" caption="Pin cross reference for AVR microcontroller and LCD" link="http://www.flickr.com/photos/mmechtley/2276172743/" class="image-packed" %}

I then soldered wires to the relevant LCD outputs on the board (the connectors were nice and big compared to the microcontroller pins). I spent a bit of time determining which outputs from the LCD I wanted to read. As it turns out, you only need five segments from a seven-segment digit to determine the numerical value of the digit -- the bottom and bottom right segments are superfluous (see [Matt Mets's recent post](http://www.cibomahto.com/?p=152), who solved the problem independently). I ran a total of eleven wires -- two digits for the BAC level and one wire for the "Wait" indicator -- into digital inputs on an [Arduino Diecimila](http://www.arduino.cc/en/Main/ArduinoBoardDiecimila). The Arduino code ended up pretty simple -- it reconstructs two digits and the status of the "Wait" indicator and transmits these serially via USB.

{% include figure.html url="http://farm3.static.flickr.com/2185/2276175019_89175e3bcd_m.jpg" alt="You only need to observe five segments of a seven-segment display to know which number is displayed" caption="You only need to observe five segments of a seven-segment display to know which number is displayed" link="http://www.flickr.com/photos/mmechtley/2276175019/" class="image-packed" %}

{% include figure.html url="http://farm3.static.flickr.com/2077/2276967352_ff39bfce04_m.jpg" alt="Soldering more wires - first digit done" caption="Soldering more wires - first digit done" link="http://www.flickr.com/photos/mmechtley/2276967352/" class="image-packed" %}

I then read the serial data in using the Java [RXTX library](http://rxtx.org/) and spit it into a text file, which I then read in from [Unity](http://unity3d.com/). The game then makes the paddle size larger the drunker you are!

{% include figure.html url="http://farm3.static.flickr.com/2240/2276970964_3fb3aeb47a_m.jpg" alt="Waiting for the player to use the breathalyzer" caption="Waiting for the player to use the breathalyzer" link="http://www.flickr.com/photos/mmechtley/2276970964/" class="image-packed" %}

{% include figure.html url="http://farm3.static.flickr.com/2382/2276180739_985c0fb33a_m.jpg" alt="Playing with Player 1 significantly drunk" caption="Playing with Player 1 significantly drunk" link="http://www.flickr.com/photos/mmechtley/2276180739/" class="image-packed" %}

The hardware is of course begging to be used in other ways -- how about a program that locks you out of Ecto and your forum accounts when you're right trashed? No more embarrassing comments that you can't take back! I may go back and make a more sophisticated game in the future -- Pong was about the right scope for the single day of development time I had left after handling the hardware and serial transmission!

I'll have the game up for play at the 9Bit indie games party Tuesday night -- if you're at GDC just find folks from [Flashbang](http://flashbangstudios.com), [Gastronaut](http://www.gastronautstudios.com), or [ThatGameCompany](http://thatgamecompany.com) to get an invite and drink tickets! I'll post an Instructable and some more information about the software when time permits. Extra special thanks to [Becky Stern](http://sternlab.org) and [Matt Mets](http://cibomahto.com) for their advising on the hardware interface!
