---
layout: post
title:  "Robot Malfactory"
date:   2017-11-22 17:49:00 +0100
categories: [Game project, Team project]
featured_image: "/assets/images/Robot Malfactory/RobotMalfactory.png"
team_size: 5
duration: 8 weeks
task: physics programmer
tech: Unity
---
The assignment for my fourth block at IGAD was to create a physics based puzzle game in Unity. The catch was that the project was not allowed to any of Unity's built in physics components. We would be working in teams of 5. With people from multiple disciplines.

<!--more-->
{% include video.html id="44nT4yy04D8" %}

I was one of two programmers on the team. I programmed all physics in the game. We split the work but unfortunately his part didn't work as well as expected. The art direction of the game changed multiple times during the block. After the last change our artists only had 2 weeks left to create assets for the game.

The game is about a malfunctioning robot (player) in a warehouse. In this warehouse robots work together to stack and sort the packages. The malfunctioning robot is instead trying to do the exact opposite. With the use of future technology the gravitational direction of the packages in the warehouse has been changed. The goal of the game is to use the stacks of boxes to disrupt the workflow of the other robots.

<h3>My work</h3>
<h4>Custom 2D physics system</h4>
As mentioned previously we weren't allowed to use any of Unity's built in physics components. I based our system on [Box2D]({{"https://github.com/erincatto/Box2D"}}). Our physics system technically only supported rectangles and spheres. We could've supported any kind of convex shape using the same code used by the rectangles but we didn't need it because of the design of the game.

<h4>Stack stability</h4>
{% include video.html id="H_4x4znJfCU" %}
With the first iteration of our physics system and even when using Unity's physics system, stacking boxes turned out to be an issue. Because of precision errors in the code, if we would leave the game running for long enough a stack of boxes would eventually fall over. I found that the issue was that the system would often generate two hit points. One on the left and one on the right side of the box. Because one contact point would be resolved before the other the first would impact the second. This caused the boxes to shift slightly causing the instability. I solved the problem by merging the contact points under certain circumstances.

<h4>Distance constraints</h4>
{% include video.html id="yU7wPi7vvtI" %}
I added distance constraints so we could have ropes in our game. Design never ended up using them unfortunelty. They worked well though.
