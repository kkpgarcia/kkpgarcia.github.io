---
layout: post
title: Luna Engine Dev Log 1
description: >
  It has been more than two weeks since I started this project. I was aiming to write a blog on how I deal things in some sort of a “major” way. Bringing big updates each time I write an entry.

sitemap: false
hide_last_modified: true
---

However, I encounter exciting challenges along the way while slowly building the project from the ground up. Hence this dev logs things.
I hate dev logs as I didn't want to talk about some minor details that I have encountered. Upon doing the project, I found out that there are actually learnings in between significant developments.

### Officially Naming the Project

Obviously, I can't keep on calling it "That stupid project of mine". I had to name the project eventually, and I chose Luna for it. There's no real deep meaning to it. I had a game engine made in C++ called Stella (name of my eldest daughter), and Luna (if I get a new daughter) is closely derived from it.
One primary reason would be that I would eventually make the engine a Typescript module, and I wanted it to have at least a name that would encapsulate the whole library. Currently, the project is in version 0.0.12 and is still far more to be in 0.1.0 at least

### Implementation of WebGL2

I initially wanted to stick with WebGL. Upon doing some research on WebGL, I found out that WebGL2 was just released recently. Of course, it is inclined more with the pro side because WebGL is starting to be a decade older than it is meant to be. Transitioning to WebGL2 would be the wisest decision.
Luna already has a solid Rendering API, and I can theoretically render 3d models with basic shaders. Lighting is still not included. There are still many things to be done in this rendering API, and those might be the most complicated part of implementing your own renderer.

### Linear Math 0.0.12

I chose to write my own math library because well… Is it fun? I believe it is the best coding practice for any game engineer. There was a lot of decision making done in this library. I eventually decided on having a unified class that would contain all math calculations in the engine.


This actually saved me time writing a bunch of basic arithmetic equations for all my needs. Given that I set the parameters as an array of numbers, it is easier for me to pass values from different components such as Vector2 and Vector3. I will have to make a separate implementation for Quaternions and Matrices, though. I haven't tackled them as of the moment, so we'll see.
A quick glimpse of how Vectors are using this implementation:

!!CODE HERE!!

This VetorBase contains functions similar to Vector2 and Vector3, such as getting the length of the vectors and dot product. Since the values of each vector is an array _val, It is easier for me to loop through the collection and return the values accordingly from the MathImpl library.
Functions that are exclusive to Vector3 is implemented accordingly:

Theoretically, each element of the array is linearly placed in the memory. If I were to retrieve these values, I would be able to take advantage of cache hits, thus making it more efficient rather than allocating each value randomly in a heap.

### Rendering API 0.0.12

The current rendering process of the Luna Engine is pretty straightforward. As mentioned above, I decided to use WebGL2. Currently, Luna's rendering capabilities are limited, though it is already highly complex. Upon testing each component, objects are already working as I hoped.
What's next for the rendering API is to have a container for shader attributes. For games, it is similarly close to the "Material" of objects. Other than the attributes, I want to create a thing and simply call the render function for simplicity.

!!CODE HERE!!

Currently, the whole sandbox takes in the data of what we want to draw, in this case, a rectangle, and create each component that is needed in the rendering, such as the buffers, shaders, and the renderer such as:

As you can see, each function that needs the gl context retrieves it from a singleton. I will need to have a way to have a global variable to eliminate retrieving the singleton repeatedly.

### Luna Engine as a Module

The whole idea of having Luna as an Engine would be having to reuse it for the other software in the plan. It also allows me to be flexible with the engine. Before exporting Luna as a module, I was having a hard time testing it properly. Obviously, I didn't need to run Luna on a server and try it in a mobile browser. It's just not efficient enough. It was indeed in my plan to have it as a module, but for later stages. I am glad that I did it now.
Having it exported made me realize that I am now able to do some proper unit testing. Having a vanilla project has allowed me to integrate unit testing for some libraries inside Luna. Primarily the math library. Obviously, I knew adding numbers is essential, but it is still the right thing to do.
Testing the rendering API would be an entirely different topic. Probably a task that I will do when I do more APIs.
The other realization that I had was the framework that I was using. I stated in the previous blogs that I was using Angular for the sole purpose that all my mobile dependency problems would already be solved. It was a deciding factor that I can easily use ionic build or some other command to build me some APK.
It was okay, but I want the project to be even more lightweight. Obviously, I will still need a third-party solution for this until It really wears me off. I am now deciding on stripping the angular framework and just stick with a capacitor. I will probably have to do more research on this. Ideally, I will only need to use a mobile framework to embed my App when building the App. Upon writing this, I think I will benefit from having my own builder for the project.

### Additional Workflow for the Project

Given that Luna Engine is now a module, I can easily import it into every project I want. However, I am not that rich enough to have a private npm registry, so I needed to host one on my own. This is where I found Verdaccio. A perfect private npm registry for my needs. It is lightweight and open-sourced. This, however, needs to run when I publish the module and retrieve it for my projects.

### For the Future

Obviously, this project is way to be for just one person. I may get tired of doing it, and I hope not. The reason why I do these blogs is for me to commit myself to do it. I don't actually intend these blogs to be read by people; I keep posting them out there as a reminder that I have a commitment to a project. So, future me, it's okay for you to stop. However, you'll be missing a lot of learning opportunity for it.
That aside, I will be continuing to implement the rendering API, and hopefully, I will be able to work on quaternions and matrices for the math library. I am still far from doing any GUI work, actually. However, I don't intend to make the imgui library stagnant.

*[HTML]: HyperText Markup Language
*[CSS]: Cascading Style Sheets
*[JS]: JavaScript
