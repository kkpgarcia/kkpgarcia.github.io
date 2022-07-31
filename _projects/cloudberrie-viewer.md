---
layout: project
title: 'Cloudberrie Viewer'
description: >
  An application of Cloudberrie where you can play the experiences that you built using Cloudberrie Builder
date: 1 Aug 2021
image: 
  path: /assets/img/projects/cb1.png
  srcset: 
    1920w: url(/assets/img/projects/cb1.png) center/cover
links:
  - title: Cloudberrie Websites
    url: https://www.cloudberrie.io/
accent_color: '#4fb1ba'
accent_image:
  background: url(/assets/img/projects/cb4.png) center/cover
theme_color: '#193747'
sitemap: false

---
---

### Technology

|:---------|:----------|
| Engine      |         Unity | 
| Language      |         C# |

![200x200](/assets/img/projects/cb4.png "Small example image")

When I got to cloudberrie, one of the projects that I wanted to fix was Cloudberrie Viewer.

### State Controlled Architecture

Since we had a small timeframe for our beta release in February 2022, I re-created the Viewer and applied a state machine architecture along with it.

### Service Locator and Services

Each major libraries that cloudberrie had was converted into a service where they can be initialized in isolation and run without any dependencies outside the services structure.

### In-house Event System

An additional library to the cloudberrie was the Notification Center, a system inspired by apple's approach to observer pattern. 

### Controller/Agent Approach to Multiplayer

When dealing with Multiplayer, we devised an approach where all communications will go through the host (controller) of the current playthrough and to the participants (agents).

### Remote Procedure Call extensions for Photon

I wanted us to deviate from using third-party tools completely for maximum flexibility. This is where our new Network Command Manager interfaces all photon rpc calls out of our codebases.

### Visitor Pattern for Instruction System

Graph is read by the viewer differently than how builder does it. It is more compact, and concise. Visitor pattern was used to run-thorugh these instruction graphs where different players have different types of visitors for them dpeneding if they are hosts, or participants.