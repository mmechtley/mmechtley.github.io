---
layout: post
title: Integrating Cocoa With Unity iPhone
date: 2009-01-23 22:39:00 -0700
categories: flashbang games iphone unity
---

I just finished writing up a post for the [Flashbang Technology Blog](http://technology.blurst.com) about integrating custom Cocoa content with Unity iPhone projects. I spent about two and a half weeks in December developing a system that would work for all of our Unity iPhone projects. The goal was to allow me to develop all of our menus and other non-gameplay content using Apple's super-slick UI development application, Interface Builder. I used this in !Rebolt! and managed to finish all the menus in a couple days. Here's a snippet:

> So I set a goal: Make an easily extensible Cocoa frontend for Unity iPhone that supports Blurst logins and supports any menus we might want. It should work for any project we add it to, so we don’t have to do tons of custom code for every game. Further, it should require changing as little of ReJ’s existing Objective-C AppController code as possible, in the event that it changed in a later build. Finally, I wanted an easy way to add my additional files to the XCode project once I created a build. This is particularly important because, to maintain rapid iteration times, there must be a minimal amount we have to do in XCode between creating a build and installing that build on the phone.

You can read my [full article](http://technology.blurst.com/a-cocoa-based-frontend-for-unity-iphone-applications/) at [technology.blurst.com](http://technology.blurst.com).