---
title: "The Next Y2K: Year 2038 Problem"
created: 2023-01-29
date: 2023-01-29
categories: 
  - programming
tags: 
  - y2k38
authors: 
  - thecd
description: "The new Y2K is the year 2038 problem, also known as the Y2K38 bug. The Unix Timestamp is to blame but there is a simple fix which is already in the works."
cover:
    image: images/the-2038-problem-y2k38.png
---

Many of us remember the Y2K bug, where all computer systems were going to crash and destroy the world. Obviously, that didn't end up happening, thanks to the hard work of programmers and systems admins around the world. The Y2K bug had to do with how dates were used in computer programs. In the early days of computing, storage space was important, so programmers had to write very efficient code in order to not use unnecessary storage space. The difference between 2023 and just using 23 was huge back in that day. By the time the year 2000 rolled around, storage space wasn't as expensive and programmers didn't need to worry about a difference between 2023 and 23 anymore.

## The 2038 Problem

Another issue has the attention of systems admins and programmers, this time it is with how time has been calculated since the 1970s on many computer systems.

The UNIX Timestamp which is also referred to as Unix Epoch, considers the start of time to be January 1, 1970. This way of time accounting starts with 0 and counts the seconds since January 1, 1970. This UNIX Timestamp is the basis for time and date calculations on many systems around the world.

The issue here is the Unix Timestamp or Epoch is stored as a 32-bit signed number. The maximum value for a 32-bit signed number is 2,147,483,647. That's a pretty big number but in terms of how it is used, this number represents seconds, a relatively small increment of time. Care to guess how many seconds have lapsed since the start of the UNIX Timestamp? At the time of writing this post, that number is currently 1,674,924,554 according to [Epoch Converter](https://www.epochconverter.com/).

We are getting close to the maximum value of a 32-bit signed number, this is the 2038 Problem. Also, known as the Y2K38 bug. So what happens when the seconds try to increment past the maximum value of a 32-bit signed number? Well, the value will start counting up again but this time it will be from its lowest possible value, which is -2,147,483,648.

See the problem here? When the Unix Timestamp reaches its maximum value, it will be like going back in time. The lowest value that it will then start counting from would be considered December 13, 1901. So all times and dates that use the Unix Epoch as a basis for calculations will have their value thrown off by this.

It's important to note that while we mention Unix here, this doesn't just impact Unix and Linux devices. This form of timestamp has been adopted by many programming languages that run software on all types of devices.

## So How Do We Fix the 2038 Problem?

The solution to this issue, some would say is simpler than the original Y2K bug. The easiest solution is for programmers to switch from 32-bit integers to 64-bit integers for storing this value. Doing so, allows the number to keep counting upward. The [Wikipedia page](https://en.wikipedia.org/wiki/Year_2038_problem) for the problem has a deeper explanation of proposed solutions and some already implemented solutions.

The thing to note here is that there is a lot of time left to solve this issue. Awareness of the issue is not an issue, as systems engineers, admins, and programmers are already working on solving the issue. No worries about the Y2K38 problem shutting down your bank or any other core systems.
