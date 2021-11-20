---
title: 'PyGame Basics: Keyboard Input'
author: Jared
type: post
date: 2019-10-05T02:27:58+00:00
url: /2019/10/04/pygame-basics-keyboard-input/
featured_image: /wp-content/uploads/2019/10/pygame-basics-keyboard-input.png
rank_math_primary_category:
  - 315
rank_math_description:
  - Learn how to retrieve and utilize keyboard input with PyGame. Get started with this bite-sized guide and learn how to use keyboard input in your game.
rank_math_focus_keyword:
  - PyGame keyboard input
rank_math_robots:
  - 'a:1:{i:0;s:5:"index";}'
rank_math_internal_links_processed:
  - 1
rank_math_analytic_object_id:
  - 12
categories:
  - PyGame
series:
  - PyGame Basics
tags:
  - beginner
  - guide
  - PyGame
  - Python
  - tutorial

---
In this guide, we will take a look at a couple ways to gather keyboard input with [PyGame][1].

There are a few ways of grabbing keyboard input. The first way to gather keyboard input is via capturing [PyGame][1] events. To check if any arrow keys are pressed down on the current update, you can write:

<pre class="EnlighterJSRAW" data-enlighter-language="generic" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">for event in pygame.event.get():
    if event.type == pygame.QUIT:
        running = False

    if event.type == pygame.KEYDOWN:
        if event.key == pygame.K_LEFT:
            print("Pressed left")
        if event.key == pygame.K_RIGHT:
            print("Pressed right")
        if event.key == pygame.K_UP:
            print("Pressed up")
        if event.key == pygame.K_DOWN:
            print("Pressed down")</pre>

To check if any arrow key is released on the current update, we can type:

<pre class="EnlighterJSRAW" data-enlighter-language="generic" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">for event in pygame.event.get():
    if event.type == pygame.QUIT:
        running = False

    if event.type == pygame.KEYUP:
        if event.key == pygame.K_LEFT:
            print("The left arrow key was released.")
        if event.key == pygame.K_RIGHT:
            print("The right arrow key was released.")
        if event.key == pygame.K_UP:
            print("The up arrow key was released.")
        if event.key == pygame.K_DOWN:
            print("The down arrow key was released.")</pre>

Another way to check pressed keys is to use the _pygame.key.get_pressed_ method. In your game loop, or update function, you could type:

<pre class="EnlighterJSRAW" data-enlighter-language="generic" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">pressed = pygame.key.get_pressed()

if pressed[pygame.K_w]:
    playery -= speed
if pressed[pygame.K_s]:
    playery += speed
if pressed[pygame.K_a]:
    playerx -= speed
if pressed[pygame.K_d]:
    playerx += speed</pre>

Unlike the previous method, this method allows you to check whether a key is down every game update. Using the _pygame.key.get_pressed_ method would allow you to easily check inputs and move your player (or any other game object) how you wish.

## Concluding Thoughts

Now you know the different ways of collecting input with [PyGame][1]. Hopefully you found this guide useful, if you have, you may want to take a look at the rest of this [series][2]. To receive news about our latest tutorials and courses we publish, consider subscribing to our [newsletter][3]. Of course, if you found this tutorial valuable, sharing it on your favorite social media platform would be much appreciated.

 [1]: https://pygame.org
 [2]: https://learn.yorkcs.com/category/tutorials/gamedev/pygame/
 [3]: https://learn.yorkcs.com/newsletter