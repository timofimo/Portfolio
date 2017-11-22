---
layout: post
title:  "Gauntlet clone"
date:   2017-11-20 15:54:00 +0100
categories: [Game project, Solo project]
featured_image: "{{site.baseurl}}/assets/images/Gauntlet/Gauntlet(1).png"
image_sliders:
  - gauntlet_images
---
The assignment for my first block at IGAD was to create a [Gauntlet]({{ "https://en.wikipedia.org/wiki/Gauntlet_(1985_video_game)"}}) like game. It didn't have to look like Gauntlet and it didn't have to play like Gauntlet. It just had to resemble Gauntlet.

<!--more-->

{% youtube 5z1mu9rgaQ0 %}

I was already experienced with OpenGL and C++ but I couldn't draw or design a game. I made a decision early on to create a Gauntlet clone and use the sprites I found online. I heavily modified and extended on the framework provided to me by IGAD. After about 3 out of 5 weeks most features were implemented. In the time I had left I added some extra features to the project.
<h3>Features</h3>
<h4>Animated sprites</h4>
All entities, projectiles and effects are animated sprites. This makes the game feel way less static.
<h4>Sound</h4>
The game has sound effects. Implemented using FMOD API.
<h4>Random dungeon generation</h4>

{% include slider.html selector="gauntlet_images" %}

All dungeons in the game were 100% procedurally generated. It supported both square and circular dungeons. No matter where the player spawned he would always be able to complete the level.
<h4>A-sync A* pathfinding</h4>
The thief uses A* pathfinding to find the fastest route to the player and to find its way back to the exit once it has stolen the players money. Because of the size of the maps and their complexity finding a path using A* could take a while. That's why I run the process on a separate thread.
