---
layout: post
title: Luna Engine Dev Log 2 - The 0.0.3 Update
description: >
  It might seem a small jump from where I was from almost a month ago, but personally, I feel like I really hit the right amount of updates during this development so far. I was planning on a different development log for the second one, but I didn't get around to finishing it due to particular circumstances.

sitemap: false
hide_last_modified: true
---

The Luna Engine 0.0.3 consists of a stable 3D Rendering API:

3D Sandbox Scene of the Engine
There's still a lot to work on like this as the process of producing this 3D scene is still incredibly rigid because I still haven't encapsulated the mesh creation process into one pipeline:


The vertices of the cube are still hardcoded. Luckily for the normals, it wasn't really that hard to calculate all of those in runtime. However, these data should come from the 3D models, such as OBJ and their material properties. Given that most GL calls are already encapsulated to their own buffers and automatically lays everything for OpenGL to read them, it will be pretty easy enough to encapsulate these into one class, maybe a Mesh class? I have yet to finalize it since I still need to understand how skinned meshes and my plans for the material system of the engine.
Another challenge for this is the scene graph of the whole 3D scene of the engine. It is pretty easy to make a graph, as I have done a ton over the years; the real challenge here is the matrix calculation of each node and how they should be rendered.

### Rendering API Problem

Okay, I don't really have a problem as of now with it, and the rendering process is still straight forward as it can be. It would be the most basic implementation of any rendering process for any graphic programs out there. However, I am still sticking to one pipeline:

* Gather Model Data (Vertices, Normals, Colors)
* Form the Data
* Add the Layout on how OpenGL should read the data
* Add the shader
* Render

That is cool and all, but I haven't really gotten to how an accurate rendering works. This pipeline is okay, but what if I add a 2D element to that pipeline? Or if I want to render an object without any data on it (using only Vertex Shader to draw)? What If I pass in an illuminating object? How will it affect other things? The current renderer only works with 3D and a single pipeline. I don't even know if I should have different channels for 2D and 3D objects. How many passes I would need for each one as well. Not to mention PBR capabilities.

### The Graph Problem

I annoyed my wife explaining this one. It is relatively easy to implement a scene graph on its own. It gets complicated when you think about the things that you haven't implemented yet. The closest related is the collision engine. Sure, what I needed to implement should be independent of this but actually doing it is more complex because I haven't really thought about handling collisions at this point.
Another thing to think about is how objects are handled by the renderer, collisions etc., in the scene graph. Do I use a command pattern? Or a visitor pattern? Or both? There aren't any substantial resources regarding game engines in general. The only resource that I have is the game engine architecture and nothing else.
I hate just going with the flow in regards to coding because it generally ends up having to refactor many things. However, this is just a personal project of mine; maybe it wouldn't hurt as much. Well, I hope.

### For the Coming Weeks

There's a lot of things to deal with in this engine. Loading 3D models is easy, but I need to set the Material System and the Scene Graph working before doing so. Matrices have been included in the math library; however, there are still computational errors when I calculate all the matrices together. Lighting kinda works, but it still has a long way to go.

*[HTML]: HyperText Markup Language
*[CSS]: Cascading Style Sheets
*[JS]: JavaScript
