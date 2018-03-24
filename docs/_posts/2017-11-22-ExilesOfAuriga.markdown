---
layout: post
title:  "Exiles of Auriga"
date:   2017-11-22 19:35:00 +0100
categories: [Game project, Engine project, Team project]
featured_image: "/assets/images/Exiles of Auriga/PromoScreen.png"
image_sliders:
  - exiles_of_auriga_images
top_post: true
team_size: 16
duration: 8 weeks
task: graphics programmer
tech: C++  & OpenGL
---
The assignment for my fourth block in my second year at IGAD was to create a game with the [Jackal Engine we created earlier in the year]({{site.baseurl}}{% post_url 2017-11-22-JackalEngineV2 %}). We were one of three engine teams that went all the way to the end of the year. We would be working in teams of 16. With people from multiple disciplines.

<!--more-->
{% include video.html id="3L5043p6jw8" %}

Yes!!! We made it to the end of the year. We made a game in an engine that was build from scratch.

The player is the commander of his own fleet. While he is in the bridge overseeing his operations, he receives a warning that enemy ships are approaching. He selects the ships he needs to defeat the incoming threat. Then he jumps into the action. Using advanced holographic technology he is put in the middle of the fight. From this view he can oversee the battlefield and control his fleet to defeat the enemy.

{% include slider.html selector="exiles_of_auriga_images" %}

At the start of the block we ran into a couple of problems. The tools were buggy and incomplete and the physics system was bottlenecking our game. I took over as our physics programmer and was still the only graphics programmer on the team. I spent the first weeks trying to speed up our custom physics engine. Then I spent most of my time fixing and adding new features in some of our tools. Of course I also helped by implementing new components and adding new gameplay elements.

<h3>My work</h3>
<h4>Physics optimization</h4>
Going into this block the physics system was complete but slow. Our implementation of an octree which we used for spatial partitioning turned out to be incredibly slow. Yet we couldn't find anything wrong with it. For comparison I implemented a BVH tree. The BVH tree turned out to be up to 300% faster. It also allowed us to do ray casts and insertion queries more easily. So we replaced the octree with a BVH tree. This made the physics system less of a bottleneck.

<h4>Tools</h4>
I spent a lot of time bugfixing and polishing the tools. The biggest undertaking was making the renderer work for the scene editor. The scene editor used a different scene graph and component system compared to the main engine. It took a couple of attempts to before everything worked as intended.

<h4>Gun</h4>
Just for fun we added a gun to the bridge that the player could pick up and shoot.

<h3>Rewards</h3>
The teachers awarded our team with the Best Game Programming award for this year.
<img src="{{ "/assets/images/Exiles of Auriga/Award.jpg" | relative_url }}" alt="Award" class="post_image">
