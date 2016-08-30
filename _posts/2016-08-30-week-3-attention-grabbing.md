---
layout: post
title: "Week 3: Attention Grabbing"
description: ""
category:
tags: []
date: 2016-08-28
---
{% include JB/setup %}

The most important thing that CS3216 is going to teach me is probably how to manage my time well. And by manage well, it's probably something along the lines of ditch-everything-and-do-3216.

And even that's not really working, with assignments 1 and 2 happening concurrently.

Assignment 1's progressing along alright, a bit slowly, but it can't be helped with Assignment 2's deadline looming. That, combined with CVWO to complete, means very little time dedicated to Assignment 1 (Sorry Varun, Yichen, and Zhi An 😞)

# Grab
Yeap, so our assignment 2 app is Grab (hi Yangshun!).
I've used it a fair bit, and I have to say the mobile app is quite slick and I don't have any major issues with the UI. So it was quite a challenge to come up with items to fulfill the "bad" and "ugly" parts of the presentation. Louie, though, has plenty to complain about pretty much everything, so he was a big help in populating that part of the presentation.

What I did enjoy, however, was coming up with the how-we-would-implement-it part. Instead of proposing the "usual approach":
- Objective-C/Swift on iOS
- Java on Android
- RoR/NodeJS for application logic
- PostgreSQL/MySQL for database

I came up with a 'serverless' architecture based entirely around the various Amazon Web Services

![How the various components interact with the app](/blog/assets/images/aws-archi.png)

Your native apps would still be built using the usual tools, but everything else would be different:

- [Amazon API Gateway](https://aws.amazon.com/api-gateway/) handles the API endpoints
- [AWS Cognito](https://aws.amazon.com/cognito/) handles authentication through OAuth or by logging in
- [AWS Relational Database Service](https://aws.amazon.com/rds/) for....you guessed it, relational databases
- [AWS DynamoDB](https://aws.amazon.com/dynamodb/) for a faster NoSQL key-value store
- [AWS Lambda](https://aws.amazon.com/lambda/) handles the API logic, which consists entirely of stateless functions that are run when particular events are triggered (such as when someone accesses the API through API gateway). Lambda interacts, through the AWS API, with DynamoDB and RDS, performs the necessary logic, and responds through Gateway.
- [Amazon Simple Notification Service](https://aws.amazon.com/sns/) can handle mass-notifications, suitable for instances such as when issuing new promo codes for a new marketing campaign.

The advantage of this would be, chiefly, scalability and reliability, since Amazon handles all the servers and storage, so you won't need a bunch of dedicated sysadmins to be managing a datacenter, or even have to manage cloud server deployment. Since everything is pay-per-use, costs scale with usage and spare capacity isn't wasted.

Plus, you can also use some of Amazon's cool cloud analytics features like Kinesis to handle-real time streaming data, which would be very useful for determining, for example, surge pricing, or for figuring out whether there are anomalous trends in rider/driver count that require attention.

I thought that was really cool, but I guess I must sound like a pretty big Amazon shill right about now. Oops.
