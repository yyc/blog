---
layout: post
title: "Welcome Back"
description: ""
category:
tags: []
---
{% include JB/setup %}

And I'm back, a full month after the last blogpost (sorry, with everything going on it's hard to find the time)

# Assignment 3 Post-Mortem

So our Assignment 3 was submitted a while back, and I've only really found the time to pen down my thoughts about it now. (Midterms, *man*).

For those that don't remember, our Assignment 3 project is **Let Me Know**, a new approach to project management based around the ideas of triggers -- 'Let Me Know X', that aims to simplify project management by modeling tasks and components in a more efficient way.

But beyond the idea, I'd like to explore what did and didn't work, in the hopes that it might help anyone trying to do something similar.

## ServiceWorkers

In the beginning, ServiceWorkers promise amazing things: background processing and updates, push notifications, and unicorns.

Okay, maybe not unicorns.

Still, the [ponyfoo article](https://ponyfoo.com/articles/serviceworker-revolution) does a great job of highlighting some of the amazing things that are in store with ServiceWorkers, among which we'd like to use Background Sync and Push Notifications the most, since they'd be what we seek in a native app, and would bring our PWA experience closer to that of a native app.

The downside of staying on the blazing edge, however, is that stuff doesn't get supported. Serviceworkers (install, lifecycle) aren't even supported on Mobile safari, Push Notifications only work on Desktop Firefox and Chrome, and pretty much nothing supports Background Sync (save Chrome on Android).

Maybe next year, yeah?

## Telegram authentication

Something that I did manage to get working, that I'm pretty proud of, was Telegram Authentication.

![Login with Telegram](/blog/assets/images/lmk-login-with-telegram.png)

As you may or may not know, Telegram doesn't offer an authentication API, so you can't typically log in directly with Telegram. Did that stop us? Of course not! Because so much of our app relied upon Telegram integration (in the form of our bot, [@lmknowbot](http://telegram.me/lmknowbot)), we wanted to make it such that you could log in solely with Telegram, without needing to first authenticate with Facebook / create an account, then link your Telegram username. Accomplishing this, however, required some creative thinking.

Authentication is all about information, so that's where we began our analysis. Telegram's bot API is structured in such a way that we can't message a user until that person first starts interacting with our bot. And there's no way to resolve a given @username into a userID (the bot API only accepts user IDs), meaning that the only way for a given telegram authentication scheme to work would be for a user to initiate contact through telegram.

Fortunately, there's a pretty standard way for users to initiate contact with a bot. If it's the very first time, the user has to first send a '/start' message to the bot in lieu of any other message, providing a convenient way for us to notice when someone is communicating with our app on Telegram for the first time. This, combined with the [Telegram URI Scheme](https://telegram.wiki/tips:urischeme), allowed us to provide a 'Log In with Telegram' button that, when clicked, opened a Telegram chat with our bot. Great!

That's only half the battle won, though. There's still the problem of logging in the actual browser session. This part is sorta-inspired by Slack's magic login links. When a user makes a telegram login request (sending /start), the bot checks the database for the user associated with this telegram user ID (and creating one if none exists). A one-time token is then created (using the very convenient [sequelize-tokenify](https://github.com/pipll/sequelize-tokenify)), and sent back to the user, taking the form of something along the lines of `https://lmk.herokuapp.com/#/app/auth/telegram?code=thetokenhere`

The user can simply click this link, like Slack's magic login links, and this will open the app again. The ionic application controller, once it loads, would take the code in the URL, send a AJAX request to /auth/telegram with the code, and get back a json web token for the user, logging the user in.
