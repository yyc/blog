---
layout: post
title: "Final Project Beginnings"
description: ""
category:
tags: []
---
{% include JB/setup %}

# Final Project Beginnings

Teamed up with Derek, Chi Thanh, and Van (continuing from Assignment 3) for the final project.
I did come up with some potential ideas for a final project, and concurrently we reached out to Bjorn, who pitched Jaedye for the internal pitching session.

## Postboard
This was an idea that I came up with when I missed a notice that was posted on OrgSync (because who checks that) and not anywhere else. As students, we get our information about school activities and classes from far too many places: IVLE, Email, OrgSync, Facebook, Telegram, etc. It can be difficult to stay on top of everything sometimes, and the fact that some things are duplicated over multiple platforms (IVLE and Email, for example) but nothing is consolidated anywhere might make it a little frustrating at times.

I wanted to build something that would manage that mess. By integrating with IVLE, School Email, and OrgSync, create a centralized "Postboard" (I was envisioning a trello-like interface) where you'd be able to see incoming notices automatically sorted by source (Module, faculty admin, external people, etc.), and let you pin things for later notice, and set deadlines. Sort of a google inbox + todo list for school platforms.

I'd also want to make a Telegram bot that can sit in on project group chats and provide functionality to automatically pin things to Postboard.

Interesting, but the scope was pretty big and ill-defined so ultimately we didn't go for it. Would still like to attempt this someday, though.

## IoT monitoring
This was kinda inspired by the RC4 (Hi Sam!) laundry bot thing that was in the news for a while. I didn't like the fact that users had to scan the QR codes to start the timers, and was wondering if there was a way to automatically keep track of laundry machine usage.

Well, there is. I came up with an initial design using an ESPresso Lite V2 and a piezo vibration sensor that would detect the vibrations from the washing machines and send usage to an online backend, which can then serve a webpage or power a telegram bot. Simple, but I wanted to do one better. Cheap microcontrollers and sensors could enable a lot of things, so I wanted to make a generic online platform in which you could create a data stream and description, be given a unique secret key, and use that to upload data from a source of your own design. Other people could search for your stream and subscribe to it.

So with cheap sensors (or whatever that served as a good proxy and could make POST requests), users would be able to monitor a variety of statistics that provide useful information, such as room illumination (indicating whether a room was occupied -- useful for things like RC lounges), Dining Hall Volume (a rough proxy for how packed it was), et cetera.

Was also ultimately rejected for the same reason, and also because we weren't sure of coming up with a successful hardware proof-of-concept while juggling the backend, telegram bot, and frontend development.

## Jaedye
We also talked to Bjorn, and set up a meeting on Monday morning at the Starbucks at Kent Ridge to discuss his proposed project Jaedye. The pitch decks he showed to us still seemed a bit jumbled up, with a lot of different ideas. But what he now seems to be interested in making is a mindfulness and attention trainer, by encouraging users not to use their phones, but to engage in certain mindfulness training exercises through audio training tracks.

This would be accomplished by having several different "modes", such as "Work", "Break", "Commute", "Meals", "Waking", etc. with a different set of audio tracks for each. These audio tracks would encourage the listener to pay attention to their body and their surroundings, becoming more present and more aware, instead of using their phones to consume "attention snacks" like social media updates or short articles during short breaks, or get distracted by chat notifications when attempting to focus during work.

![Jaedye Training Screens](/blog/assets/images/jaedye_training.png)

There's also a gamification component in the form of an egg hatching mechanism. When you set a timer for a set amount of time to work/break/commute/eat, an unhatched egg appears onscreen. This egg hatches into a cat if you succeed, and turns into a fried egg (i.e. gets broken) if you fail and switch out before the time is up.

It's partially inspired by [Forest](http://www.forestapp.cc/), another app that aims to train your attention and help you to concentrate.

Bjorn wants us to work on the Android version of Jaedye, concurrently collaborating with his team working on the iOS version, so that both can be released simultaneously. Our marketing component would be done mainly to target students from NUS who almost definitely need such an attention training app, heh.
