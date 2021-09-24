---
title: "Chunk Caching"
date: 2021-09-24T09:09:32-07:00
draft: false
description: "Caching chunks for performance"
image: "posts/003-devlog/hero.PNG"
tags: ["Code improvements", "Rendering", "Chunks"]
archives: ["2021/09", "Devlog"]
---
![Hero image](/posts/003-devlog/hero.PNG)
This weeks update is going to be pretty short as I didn't do much on the project. I worked to update the chunk rendering system to render chunks instead of individual tiles. I also started caching the vertices of chunks so that if a chunk has previously been displayed, the vertices don't need to be recalculated every frame. I also made it so that updates to window size are reflected, however this still needs to be moved to a translation matrix instead of recalculating vertices based on window size. This change will also simplify the code that's generating the vertices, removing a bunch of math to have straight forward constant locations for tiles.

# What was built this week
* Window resizes are now taken into account when rendering
* Chunk vertices are cached improving performance and making it easy to hit 240 fps
* Benchmarks for vertex generation for chunks

# What went well
* Was able to relax and spend time with family without having to worry about deadlines or what I would need to catch up on

# What could be improved
* The rendering/chunk system is getting to the point where I should probably create an architecture and start documenting things

# Goals for next week
* Move screen size changes to a matrix
* Begin implementing a separation between game state and display state
  * This will be the start for making the engine capable of multiplayer
* Normalize image sizes for this blog
