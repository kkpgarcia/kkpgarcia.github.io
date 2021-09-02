---
layout: post
title: A Long Term Personal Project Part 2
description: >
  It has been years since I have started my personal projects once again. I have been busy working on my master’s degree in computer science, which I have completed last March 2021, and settling in on my job (Just had one last October 2019 after months of looking). I guess this is pretty much the time to work on something that I could improve on.
sitemap: false
hide_last_modified: true
---

The key to any software development is planning and design. I tend to follow that structure to best tackle this project that I have. As I mentioned in the first part of this blog, I plan to do these things:

* Game Engine
* Game Editor
* 2D Animation Tool
* Sound Editor
* Pixel Manipulator Tool (For drawing) (maybe)

Of course, these would take me years, or I will be needing people to work with me. That's the ideal setup. However, I plan to work on this alone and push it publicly on GitHub if anyone is willing or have a little time to suggest a few things for these suites.
It would take a while to design most of these, and the initial plan is to create a common ground for each of these tools and work on them first.

### Common Structure

These applications should run on an android device, and each of them will be built in Ionic Framework and Typescript. I have decided on these two because these are the most accessible framework and languages I could use using my tablet. The commonality of these tools is that all of them has to have the ff:

* I/O
* GUI Library
* Real-time capabilities
* Memory Management
* Rendering Engine
* Input Management
* Math Library
* Debug and Assertions
* Profiling
* Serialization and Parsers
* Resource Management
* Event System
* Module Startup and Shutdown

Looking at the lists above, this is actually part of Jason Gregory's Game Engine Architecture book list. Surprisingly enough, these systems can be used in different applications. Hence this can be a high-level design of what the game development suite will be built on.

### Rendering

Most of the systems listed above are self-explanatory. One system that will be needed to tackle is the rendering aspect. Designing a renderer is no easy feat. Whenever I try to make my own renderer, I do make a lot of mistakes around it. The suite will use WebGL for its rendering and will mainly focus on 2D. There's no other way of explaining why I chose it, actually.
The exciting thing that needed to be discussed here is the GUI library. I am a big fan of Dear Imgui, and if I have the patience enough to use it in Termux or in this project, I would. However, I did try to use it but getting blockers due to the limitations of the Linux emulation. I did find the js implementation of imgui; however, I was not a fan of it.
Given that I am going to pursue this kind of project, I might learn to write my own Imgui Library, right? This is probably one of the first things that I will need to cross off in the list and probably be the first system that I will be designing.
Following the idea of dear imgui, I am clinging to the notion that the imgui I will do would be rendered agnostic. However, I am not that confident that I will do something as lightweight as dear imgui. I will have to experiment on having one renderer first before making my own imgui render agnostic. It is easier for me as well.

### Starting Up and Shutting Down

This is probably one of the most basic of a computer program. It is actually one of the first things discussed by Jason Gregory in his book, and I understand because I was also a victim of not minding how to properly initialize and exit my programs. Rookie mistake.
Understanding the importance of this makes you a better programmer. There is no unique way of doing it, or as other developer says, no right way of doing it. Making sure that your program initializes and exit gracefully makes you a good developer already. This would be stressed out even more if I use a language that doesn't have a garbage collector in it. But it is still a good practice for any developer's out there.
I had to make sure that my games start and end as intended when I was doing instant games on Facebook. Most people might be familiar with it, but instant games on Facebook have many entry points. The usual entry point to any game is to start it by clicking on an icon. It is the same with games on your phones. However, instant games can start from anywhere: sharing, in a group, post, etc. As I remember, each of these entry points has different contexts, which needs to be handled each time differently.
In this case, however, starting up/shutting down the applications that I plan to work on won't be as tedious as I described when I did instant games. I do not have a solid plan yet on how to do this, but upon looking at other engine's examples, such as Ogre, it has a manager that sequentially starts up its modules from the ground up when initialized and does the same thing in reverse when it needs to be shut down.
The main goal is to get the whole system up and running; there are elegant solutions for this process, such as having it queued or having a system that constantly checks for each system's dependencies. For starters, though, I might initially start them sequentially on one script and see a need to have more complex procedures later on.

### Compilation

This is one of the main blockers of this project. Mainly though, for the editor part.
As we are all familiar with how engines work, such as Unity, every change you make in the scripts needs to be re-compiled. Given that I will be using a language that only needs to run in an interpreter, I might just get away without re-compiling the project for every change I made.
However, this creates another problem for me to tackle: How the hell would I be able to run my game-specific scripts in a stand-alone application? Upon further thinking, I realized that I am working on a web-based application. Since I will use javascript and my scripting language, I can theoretically run it on my application's web-view. This, however, will need to have a particular injection to the currently running application; maybe then I may be able to pull this off somehow. Will need a lot of RND for this to work perfectly!
While talking about the compilation while making the game, the engine would be compiling the whole game for release. Again, this is a tricky problem that needed to be addressed in the earlier parts of the project.
Following the current strategy on how I work and how hard enough to compile things in an android, CI/CD will be the best option. We just need to upload a project somewhere and trigger the build server to build an app, and poof, we have an installable game!
It sounds easy enough, but it is actually complicated. Compiling the project to a working game will need a lot of work, such as stripping the project to only use the engine specific parts of the editor, coming up with a template that will contain the game, having a server that will receive the project AND triggering the build server to build the project. This, however, doesn't include assets just yet.

### To Math, or not To Math?

There are a ton of math libraries out there. I am inclined to use existing ones because these libraries have already proven their worth; they are incredibly efficient for the system and me. I would lie if I said I am good at linear algebra, but using a library is a win-win situation. Or is it? I stumbled upon Harold Serrano's game development blog in which he might have stated that it isn't better to write your own math library, but it gives you more benefits than using other's.
I have written most of the math libraries of my previous engine myself, which mostly is just looking up equations, translating them to code, and cross-referencing other math engine implementations as well. Might Harold be really on to something here? My sole purpose in writing these applications is to learn, which is what I will do.
It's the not most efficient way to do it, but I will write my own math library. I've been looking into some other engine's math library and see how they implemented it, and indeed, I have picked up on some implementations for it. More than this, I might need to have more book references on linear algebra!

### For the Future

These topics that I mentioned above are the biggest problems that I have for this project, and I will tackle them one by one as I go along with the project. I might not have encountered other problems yet. For this project, I will try to do some weekly or bi-monthly write-ups on what issues I had, how I tackled them, and the references I used. For sure, I will be talking a lot about the design of each system that I listed above. As for the project itself, I don't intend to make them public since I am still in the early stages. I don't have an official setup yet, and I am just doing sandbox on some theories.
For the record, this is what the project currently looks like:

It's still just experimental. I have a working WebGL implementation (pretty straightforward), and the app is running already as an android application using an ionic framework. Behind that is Codemagic, as I mentioned in the previous post, which is where I build my APK. After my initial RNDs on the framework and workflow, I will move to a new project and segregate libraries to their own projects.
As of now, I have the event system working and starting on the math library. I don't have plans yet to discuss how I implemented these two, but I might brush on a bit on different topics. The first primary system that I will be working on is the IMGUI Library, and I will be posting a design theory (of my own about other libraries) on it. As I mentioned before, it is not ideal for me to write my own. Still, I am curious about how it can be implemented, make it efficient, and overall, make it work.
Implementing an IMGUI already contains a lot of systems working together. You have the math, the renderer, the events, the input, the entities and etc. This will be one solid check on my overall checklist!

*[HTML]: HyperText Markup Language
*[CSS]: Cascading Style Sheets
*[JS]: JavaScript
