---
author: "Vitiock"
title: "First Post"
image: "img/first-post-thumb.png"
draft: false
date: 2021-09-10
description: "Introducing Lost Oasis"
tags: ["Procedural Generation", "Rendering"]
archives: ["2021/09", "Devlog"]
---

![demo](/img/first-post.png)

This is the first post of what will be a dev log to document my process of making a game. I'm mainly using this as a mechanism to hold myself accountable and insure that I am making progress towards goals. This is likely to look an awful lot like a sprint retrospective in the start as I learn what makes a good post and what doesn't.

I will also likely use this space at times to talk about general computer science related topics and the experiences I've had as a developer.
# What was built

Over the last week I've started several things

* A basic tile set with which to build things
* A library for managing map state
* A renderer that can render maps
* a procedural map generator
* This website

Example Island 1                | Example Island 2              | Example Island 3               |
:------------------------------:|:-----------------------------:|:------------------------------:|
![Island 1](/img/island-1.png)  | ![Island 2](/img/island-2.png)| ![Island 3](/img/island-3.png) |

# What went well
this week was fairly short as I only worked on things for 2 days. Several systems were started giving a base to build out features. Basic unit testing was also implemented across all of the new systems.

# What could be improved
I don't really have a plan, I have an idea, and I'm programming but I don't have a roadmap, or a plan to actually arrive at the finish line.

While I am unit testing my code, the code to test rendering, only minorly tests it. The code outputs images, but it doesn't yet do comparisons, or put the images in a directory so that the updates are visible in github. This means that changes to what actually gets output to the player isn't currently being tracked in a meaningful way.

Benchmarking of functionality is also sorely lacking. Some of the tests could be used for benchmarking however there isn't a meaningful way to track and compare the changes in performance.

The website for the dev log is pretty generic, and needs enhancements to make it better for posting about development progress and showing changes.

# Goals for next week
* Move rendering tests to integration to improve speed of iteration
* Create a system that maps from terrain to tiles
* Merge the code for surface rendering with image rendering
* Run tests on merge in github
* Improve screenshots within the website
  * Enable lightbox for screenshots
