---
title: "Laravel Nuts and Bolts - 2: MVC Architecture"
date: 2022-01-08T22:07:56+0000
draft: true
categories:
    - Laravel
series:
    - Laravel Nuts and Bolts
---

## An Introduction
In this part of _Laravel Nuts and Bolts_, I will be explaining the architecture that Laravel applications are built on and the pros and cons of using it.

## Application Architectures
An application architecture is a architectural pattern that determines the structure of how a software application is built.  It is a system for organizing an application, specifically in regards to it's code.

In layman's terms, you could kind of think of yourself making sugar cookies.  An application architecture are the cookie cutters which organize the code (dough) into shaped cookies.  Using cookie cutters (generally) make cookies look better than just pushing dough together into a shape.  With an application framework, your code will (generally) be more maintainable than just throwing code together in a hodge-podge way (spaghetti code).

## The MVC Architecture
MVC stands for _Model, View, Controller_.  Models handle the application logic.  Views show information, from models, to the user.  Controllers control the access models have to data.  Controllers also sends a signal the view when data is changed.

## Pros and Cons
The MVC architecture has many pros and some cons.

### Pros
#### More efficient development:
Since logic, views, and data are seperated in an MVC architected application, one developer can work on, say, the logic of an application, and another can work on the views.  MVC creates a standard separation of each part of the application which makes it easier to keep the work seperate for multiple developers.  This is known as _separation of concern_.

It's the standard structure of MVC which can make it extremely beneficial to use.  MVC can help in debugging because it can help narrow down the location of a bug, too.

#### Code is Decoupled
With MVC, the functionality of code is decoupled.  Each part of the application is separated from each other.

#### Easier Maintenance
Since code is decoupled, providing a seperation of concern — it is easier to maintain and scale over time.

#### Multiple Views
In an MVC application, models can have multiple views.

### Cons
#### Ambiguity Can Cause Issues
It can be difficult to figure out of code belongs.  There might be some code that doesn't really belong as a view or a model.  Adding the code to a controller may not solve this problem, but negate the organizational benefits of using MVC to begin with.  Additional files that don't fit models, views, or controllers can complicate things dramatically.  Files such as templates or helper files can cause issues down the road.

#### Event Driven Debug Difficulties
Due to the nature of MVC, it's easy to create an event-driven user-interface.  This can make debugging an application more difficult.

#### Theoretical Flooding of Renderer
Theoretically, views might receive a large amount of update requests which may make displays longer to render.  The view might fall behind as updates requests are received.

#### Requires Developers to Adapt
MVC introduces higher levels of abstraction.  In turn, developers have to learn and adapt to the decoupled nature of MVC.

## Takeaways
In the real world, it's important to consider the pros and cons of anything related to application development.  In the case of application architectures, despite it's potential downsides, the MVC architecture can be an amazing way to architect your application.

## In Conclusion
Luckily, Laravel makes it easy to use MVC, partly because applications are setup in this structure after running the Laravel build command.

In the next part of _Laravel Nuts and Bolts_, I will be providing an overview of a starter Laravel application.  I'm going to do my best to break down how models, views, and controllers are applied in a Laravel application.  You can find the next part of _Laravel Nuts and Bolts_ [here](https://learn.yorkcs.com/posts/2022/laravel-nuts-and-bolts-3/).