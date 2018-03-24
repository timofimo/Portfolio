---
layout: post
title:  "Jackal Engine V2"
date:   2017-11-22 19:29:00 +0100
categories: [Engine project, Team project]
featured_image: "/assets/images/Jackal Engine v2/Logo.png"
top_post: true
team_size: 8
duration: 8 weeks
task: graphics programmer
tech: C++, OpenGL & Vive
contributions: [Renderer, OpenVR support]
---
The assignment for my third block in my second year at IGAD was to create a game engine focused on a specific game genre. We were one of the engine teams that were allowed to continue working on their engine this block. We got a few extra members and added virtual reality to the project.

<!--more-->
{% include video.html id="-suy5nI2_uY" %}

With the new team members I was still the only graphics programmer on the team. We were now a group of 7 programmers.

We changed our target game to be a 3D space RTS in VR for this block. We added VR because the teachers, designers and artists all showed a lot of interest in such a project.

I learned some new tricks since the end of the last block that I wanted to try out. Because of VR we also wanted to switch to a forward renderer so we could use MSAA. Because of this I rewrote the entire renderer. Since I was rewriting it anyway I figured that we might as well switch to OpenGL. With the help of OpenVR we had our engine working with the HTC Vive in less than two weeks. The rest of the block I spent my time optimizing the rendering pipeline and adding all the features we thought we were going to need to make a game with our engine.

<h3>My work</h3>
<h4>OpenGL renderer</h4>
Much like the DirectX11 renderer from last block I made use of uniform buffers, instancing, batching and draw call sorting to make every draw call as efficient as possible. This time we were going for a forward renderer instead of a deferred renderer. This eventually became a forward+ renderer.

<h4>HTC Vive</h4>
<img src="{{ "/assets/images/Jackal Engine v2/Screenshot.png" | relative_url }}" alt="Screenshot" class="post_image">
We only targeted the HTC Vive because it was the only VR headset available to us for this block and we wanted to make use of the room scale tracking. Rendering to a VR headset and tracking the players movements turned out to be incredible easy. With the OpenVR SDK this only took a couple of days.

Since it's very important to stay above 90fps and because of the high resolutions we were working with I had to spent some extra time optimizing the renderer. I used an occlusion mesh to stop the game from rendering unseen pixels. I played with different resolution render targets and upscaling techniques.

<h4>Order independent transparency</h4>
We wanted to have a lot of effects in our game such as explosions, lasers and engine trails. Because of the fully dynamic scenes we were aiming for we couldn't reliably sort them from back to front. This meant that we couldn't render our transparent objects the conventional way. Because of that I decided to implement [Weighted, blended order independent transparency]({{"http://casual-effects.blogspot.nl/2015/03/implemented-weighted-blended-order.html"}}). The techniques is definitely not without its problems but it ended up fitting our needs very well.

<h4>Component based particle systems</h4>
Since our game was going to have a lot of effects we needed a good way to make them editable by the artists. To accomplish this I implemented component based particle system based on [this]({{"http://www.bfilipek.com/2014/04/flexible-particle-system-start.html"}}) blog post. By using this we could mix and match any number of generators, emitters and updaters to create a lot of different particle systems. Performance wasn't an issue. A team member later created a visual particle editor to expose this system.

<h4> Tools</h4>
During the first block the tool programmers used QT to create their editors. They hated QT so much that we had to find a replacement. I implemented [Nuklear]({{"https://github.com/vurtun/nuklear"}}) in our engine and made a small demo project to check how usable it was. I could create an entire tool in just two days using it. This was a big step up from QT and it had the added benefit that everything was in-process. This made it way easier to expose the renderer to the tools. We ended up using it for the next two blocks. Our entire asset pipeline was made using Nuklear.
