---
layout: post
title: "Seminar Critique: Prisma"
description: ""
category:
tags: []
---
{% include JB/setup %}

## Summary

Prisma is a recent (launched in June 2016!) photography app that goes one step beyond simple color-manipulation filters, and does sophisticated image analysis to recreate images in the form of famous art styles. In effect, it allows users to "turn every photo into art".

How it works is simple, a user takes a photo, picks a "filter" based on an existing style (typically exemplified in a particularly famous work -- The Scream, The Great Wave off Kanagawa, etc.), the photo is sent off to the server for processing, and the rendered photo is returned to the user, for his/her sharing pleasure on a variety of social networks.

Group 5 also provides some suggestions for how they would implement Prisma if they had to do it themselves, namely, to use Google's Tensorflow to construct the Convolutional Neural Network that powers the image manipulation algorithm. However, it may be prudent to consult the existing research on the particular form of image manipulation ([A Neural Algorithm of Artistic Style (Gatys et al., 2015)](https://arxiv.org/abs/1508.06576)), which the founders of Prisma probably based their app on). Implementation could also be expedited by building on existing open-source implementations, such as (this Github project)[https://github.com/jcjohnson/neural-style] which implements the algorithm outlined in the paper.

A notable problem with Prisma that the group raised was that Prisma claimed a license over the images that you use with their app. Digging into their terms of use, I do find the following:

>Prisma does not claim ownership of any Content that you post on or through the Service. Instead, you hereby grant to Prisma a non-exclusive, fully paid and royalty-free, transferable, sub-licensable, worldwide license to use the Content that you stylize on or through the Service, subject to the Service’s Privacy Policy...

Which some people may naturally find problematic.

## Takeaways
![](http://findlayfoods.com/images/stories/chinese-takeout-container_copy.png)

Reflecting upon the presentation, two parallels stuck out to me: Hipstamatic and Snapchat.

The first, Hipstamatic, was Apple's very first App of the Year. Like Instagram does now, Hipstamatic offered a (then) novel experience in making image enhancement easy and painless, making the creation of "artistic" images accessible to every person with a smartphone. For a while, it did get a huge volume of downloads and rave reviews, it ultimately lost out to Instagram in terms of userbase.

Contrast this with Snapchat, which now has its facial-recognition filters as a key feature, and sponsored, location-based filters as an effective cornerstone of their monetization strategy. However, it didn't always start out this way. In fact, for much of Snapchat's existence, it was simply a very easy way of sharing one-time photos and videos with other people, with the filters coming only much later.

Prisma actively piggybacks on Instagram to provide social features to its users, which is sensible, since much of its userbase would already be accustomed to sharing images on Instagram.

However, that also makes me inclined to lump Prisma with Hipstamatic, because they function well as proofs-of-concept of an image enhancement/manipulation technology, but without a core social feature that aids in user retention. Much of their appeal lies in their novelty and creation of interesting images, rather than in any long-term value to the user.

This can be contrasted with Snapchat and Instagram, which function primarily as communicative tools, and secondarily as image-enhancing tools. In this way, they leverage on social network effects to retain users while having an easy way (i.e. new filters) to continuously provide new experiences to users.


### Conclusion

If Prisma is to have a goal to eventually become a social platform (disclaimer: which it might not be), it might be prudent for it to take these factors into account. That said, Instagram has a huge advantage in the image-sharing space, and it may be an unwise use of resources to attempt to enter that space. Perhaps, as group 5 suggests, Prisma might find it more promising to develop innovative applications for their algorithm, such as in delivering Virtual Reality experiences, or in enhancing videos that previously had to be hand-drawn.
