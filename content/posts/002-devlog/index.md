---
title: "2D Tiling"
date: 2021-09-17T11:02:29-07:00
draft: false
description: "How tiles currently work"
image: "posts/002-devlog/hero.png"
tags: ["Procedural Generation", "Rendering", "Tiles"]
archives: ["2021/09", "Devlog"]
---
![Hero image](/posts/002-devlog/hero.png)
This week I worked on making it so that given a set of terrain, the tiles would line up and have smooth transitions between them, instead of just being squares with hard edges. This was a lot of work because I wasn't ready for how many different tile variations there were between just two types of terrain. To understand how to render an individual piece of terrain we need to look at all 8 surrounding neighbors. We then match this against a map, with just 2 types, there are 255 different combinations of tiles that we could have, as we have 8 neighbors that can exist in 2 different states each. If we had tiles that interacted with 3 terrains, then we could need 3^8 tile permutations, or 6561 (a problem I'll have to solve for at a later time, though shouldn't hinder making progress at this time).

For the examples I will be showing a 5x5 matrix of terrain colors along with the resulting 3x3 rendering of the tile.

Terrain                                         | Tiles                                                |
:----------------------------------------------:|:----------------------------------------------------:|
![Island 1](/posts/002-devlog/plus_grid.png)    | ![Island 2](/posts/002-devlog/grass_water_plus.png)  |

As can be seen in the image above that just looking at cardinal directions isn't enough because we need to be able to divot in the corners of the center piece based on the corner adjacent tiles. To figure out what tile to use, I've set a map that matches the 9 tile hash to a tile id. The code that creates the 9 tile hash currently assumes there are 3 terrains, and that water is the default. We then assign values to each quadrant in 9 tile section based on the terrain it's in.

![Island 1](/posts/002-devlog/plus_grid_with_index.png)

By adding up the red numbers in the grid we get a unique identifier that represents what area in the 3x3 grid is covered in land and which is covered in water, which can ultimately be mapped back to a single tile.

It is likely that this system of mapping terrain to tiles won't be the final form of the game simply due to not being able to scale to the multiple different terrain types I want to have present on a single map (water, sand, grass, gravel, dirt) which would be a mapping of 1953125 potential tiles even if we assume through rotation and duplication we only need ~25% of those, that's 488281 tiles, or approximately a texture with 700 tiles by 700 tiles. However being able to support several terrains now with only minor graphical issues when there are 3 terrains in an area should be enough to estimate if the prototype of the game I'm making is fun.

# What was built this week
* A mapping to determine the correct tile to use given a set of 9 terrains.
* The screenshot and window rendering were unified to a single code path.
* Unit tests are now run before each commit using git hooks, as well as when a pull request is submitted.
* Many new tiles were created for transitions between grass and water.
* Controller input now works to navigate the map in the executable.
* Vertices for a tile location are now stable as we move the camera instead of the map.

# What went well
* Got visual progress and event got some extra done with controller input
* Rendering tests made it easy to detect and diagnose when I was only using 15 of 16 pixels of each tile

# What could be improved
* Didn't get lightbox implemented in the website
* Still not confident writing blog entries I'm sure it will get easier with time and I'll feel more confident in it.
* Morning motivation/discipline is lacking though I feel motivated at night

# Goals for next week
I'll be spending a bunch of time next week with family so won't likely accomplish a lot so have reduced goals and expectation

* Performance improvements
  * Caching of chunk vertices
  * Having last updated tick in chunks to determine if recalculation is needed
* Resize rendering on window size change
* Scrolling map based on keyboard input instead of just gamepad
* Flesh out a more public roadmap of features    
