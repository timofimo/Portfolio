---
layout: post
title:  "Jackal Engine V1"
date:   2017-11-22 17:59:00 +0100
categories: [Engine project, Team project]
featured_image: "/assets/images/Jackal Engine V1/Logo.png"
---
The assignment for my first block in my second year at IGAD was to create a game engine focused on a specific game genre.  We would be working together in groups of 4, all programmers. We picked 3D space RTS as our genre inspired by games such as [Homeworld]({{"https://en.wikipedia.org/wiki/Homeworld"}}).

<!--more-->

The best engines would be allowed to continue to block C. The best of those would be used to create a game in block D of the same year. I would be working as a graphics programmer together with one engine programmer and two tool programmers.

This block I would be working with DirectX 11 for the first time in years. It took me a couple of days to translate my knowledge of OpenGL to DirectX but it didn't take long to get a deferred renderer up and running. The rest of the block I spent most of my time optimizing the renderer and implementing post processing effects.
<h3>My work</h3>
<h4>DirectX 11 renderer</h4>
For this block I wrote an all new DirectX 11 renderer. I made extensive use of constant buffers, instancing, batching and draw call sorting to make every draw call as efficient as possible.

<h4>View frustum culling</h4>
To further improve the performance of our rendering pipeline I tried view frustum culling. It gave us a huge boost in performance in most scenarios. I don't think I will ever make a renderer without it anymore.

<h4>Bloom</h4>
<img src="{{ "/assets/images/Jackal Engine V1/Bloom.png" | relative_url }}" alt="Bloom" class="post_image">
To make the lasers, lights and explosions pop even more I added a very aggressive bloom to the renderer. At first I had I bug in my code that caused the light to leak in only the horizontal and vertical directions not diagonally. After fixing the issue we thought it looked worse, so we changed it back.

<h4>FXAA</h4>
<img src="{{ "/assets/images/Jackal Engine V1/FXAA.png" | relative_url }}" alt="FXAA" class="post_image">
With out deferred renderer we had a lot of aliasing on the edges of our objects. We wanted our game to look dreamy which meant that it didn't matter that much if the edges looked soft. In our case FXAA was the perfect anti-aliasing method. It's fast, easy to implement and the artifacts it creates fit our engine.

<h4>SSAO</h4>
<img src="{{ "/assets/images/Jackal Engine V1/SSAO.png" | relative_url }}" alt="SSAO" class="post_image">
I had some time left at the end of the block. In other games ambient occlusion always is a huge improvement in the visual quality of the game. So I wanted to give it a try.  I didn't take long to get it to work. The effect wasn't really visible in our test cases but that was expected.

<h4>Camera motion blur</h4>
{% include video.html id="WKjzYp4F2VY" %}
For the same reasons as why I implemented SSAO, except for the huge improvement in quality, I decided to implement camera based motion blur. It was easy to implement. Oh boy did it make us sick.
