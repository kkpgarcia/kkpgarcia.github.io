---
layout: project
title: 'Cloudberrie Builder 2.0'
description: >
  An application that lets you create a VR Experience and run it in the VR Application of Cloudberrie
date: 18 July 2022
image: 
  path: /assets/img/projects/cb-builder-2.png
  srcset: 
    1920w: /assets/img/projects/cb-builder-2.png
links:
  - title: Cloudberrie Website
    url: https://www.cloudberrie.io/
accent_color: '#4fb1ba'
accent_image:
  background: '#193747'
theme_color: '#193747'
sitemap: false

---
---

### Technology

|:---------|:----------|
| Engine      |         Unity | 
| Language      |         C# |

Builder 2.0 is the third iteration of Cloudberrie Builder. Since Builder 1.0 is an extension of the prototype of Builder, there were a lot of techinical debt that was inherited. It was getting hard for developers to fix and improve upon the existing base of the builder.


### Contextual and State Controlled Architecture Design

The biggest challenge of Builder 2.0 was creating it from scratch, and creating an architecture fit for interchangability, and testability. Contextual and State Controlled Architecture (CSCAD) is an idea combining how .NET handles bindings and Flux architecture from JS as its data flow, and finally everything is handled by a State Machine.

### Manipulation System, an in-house input handling

Along with the new architecture design, I developed a reusable system where we can reuse input handling for different UI, and open us to late bindings called the Manipulation System.

### Observable Model Library

Inspired by Reactive Library where we can observe for variables inside classes and react to them.

### Command Binding Framework

An executable command that is reusable around the application and can be binded either to keys using Key Command Binder, or our in-house event system.

### Injection Framework

In-house inversion-of-control container that resolves dependencies.
