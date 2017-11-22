---
layout: post
title:  "Battleships++"
date:   2017-11-22 17:26:00 +0100
categories: [Engine project, Solo project]
featured_image: "/assets/images/Battleships++/Battleships++-logo.png"
image_sliders:
  - battleships_images
---
The assignment for my third block at IGAD was to create a game based on the classic board game [Battleships]({{ "https://en.wikipedia.org/wiki/Battleship_(game)"}}). The main goal of the block was to teach us OpenGL and to teach us the basics of networking with [RakNet]({{ "http://www.jenkinssoftware.com/"}}). We would be working on the project alone but everyone would be using the same server. The rules of the game where dictated by the logic on the server.

<!--more-->

There were problems with the server from the start of the block. I started early creating my own OpenGL renderer. This meant that I had a lot of time to learn new graphics techniques and implement them. I didn't start on gameplay or networking until most of the problems with the server were fixed. I still managed to implement most of the gameplay and networking logic but because of bugs in the server a game could never be played to completion.
<h3>My work</h3>
<h4>Custom math library</h4>
The teachers wanted us to implement our own math library. By doing this I learned how to use cross and dot products, "read" matrices and use matrices to take a point from one space to another.

<h4>Deferred renderer</h4>
Early on I decided to go for a deferred renderer instead of a forward renderer. I only had one directional light in the game and I ended up also implementing a forward rendering pass for all the transparent objects I had in the game. It might not have been the best decision but I still learned a lot from doing it.

<h4><a href="https://www.cs.bgu.ac.il/~grinshpo/PersistentGridMapping.pdf">Persistant grid mapping for ocean rendering</a></h4>
<img src="/assets/images/Battleships++/Persistant grid.png" alt="PersistantGrid" class="post_image">
I found this paper a couple of weeks before the start of the block. I was very interested. When we got the the assignment I immediately knew I wanted to try it out. I used it to render the ocean in my game. This was the first time I ever had problems with floating point precision. It took quite a lot of debugging but the end result was acceptable.

<h4>Cascaded shadow mapping</h4>
{% include slider.html selector="battleships_images" %}
The first time I implemented shadow mapping was also the first time I implemented cascaded shadow mapping. Because of the large draw distances in my game normal shadow maps wouldn't cut it. With all light in the scene coming from a directional light it was an easy decision to go for cascaded shadow mapping. The further improve the result I also implemented PCF soft shadows.

<h4>Screen space reflections</h4>
<img src="/assets/images/Battleships++/screen space reflections.png" alt="Screen Space Reflections" class="post_image">
My implementation had a lot of artifacts and was very slow but it did work. It made the ships look like as if they were in the water and not on top.

<h4>Particle effects</h4>
<img src="/assets/images/Battleships++/particle effects.png" alt="Particle effects" class="post_image">
This was also my first time implementing particle systems. I learned important basics such as that transparent objects have to be rendered back to front and how to make a quad always face the camera.

<h4>RakNet</h4>
This was my first time doing any networking. RakNet made it very easy to get a simple game up and running. To bad we had server problems. Otherwise I'm sure I could have had a working game.
