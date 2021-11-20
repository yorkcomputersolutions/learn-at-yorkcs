---
title: 'PyGame Basics: An Improved Game Loop'
author: Jared
type: post
date: 2019-10-15T04:19:31+00:00
url: /2019/10/15/pygame-basics-an-improved-game-loop/
featured_image: /wp-content/uploads/2019/10/pygame-basics-an-improved-game-loop.png
rank_math_primary_category:
  - 315
rank_math_description:
  - Learn to create a PyGame game loop with delta. Utilizing delta time allows you to move objects at a constant rate despite frame rate differences.
rank_math_focus_keyword:
  - PyGame game loop with delta time
rank_math_robots:
  - 'a:1:{i:0;s:5:"index";}'
rank_math_internal_links_processed:
  - 1
rank_math_analytic_object_id:
  - 10
categories:
  - PyGame
series:
  - PyGame Basics
tags:
  - beginner

---
In this guide, we will be creating a [PyGame][1] game loop with delta time. Using delta time can be very useful in keeping the movement of your game smoother. Essentially with a delta time based game loop, game objects will appear to move at a constant speed even when the frame rate changes.

Something like the following is common for a PyGame game loop:

<pre class="EnlighterJSRAW" data-enlighter-language="python" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">self.clock.tick(self.fps)
while not self.done:
    self.update()
    self.render()</pre>

To convert this game loop to utilize delta time, change the above code to the following:

<pre class="EnlighterJSRAW" data-enlighter-language="python" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">dt = 0
self.clock.tick(self.fps)
while not self.done:
    self.update(dt)
    self.render()
    dt = self.clock.tick(self.fps) / 1000.0</pre>

Then whenever you&#8217;re updating the position based on velocity, multiply the velocity by the delta time of the current update. Here&#8217;s a quite example of what I mean.

Usually, you could type this to move an object to the right:

<pre class="EnlighterJSRAW" data-enlighter-language="python" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">self.x += this.speed</pre>

With a delta time based game loop, can add a multiplication operation with the delta time.

<pre class="EnlighterJSRAW" data-enlighter-language="python" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">self.x += this.speed * dt</pre>

Of course, you will need to add a delta time parameter to your update method declaration.

<pre class="EnlighterJSRAW" data-enlighter-language="python" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">def update(self, dt):</pre>

So the final example code would look something like:

<pre class="EnlighterJSRAW" data-enlighter-language="python" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">def update(self, do):
    self.x += self.speed * dot</pre>

Hopefully this guide has helped you to create a [PyGame][1] game loop with delta time. If it has, you may be interested in the rest of my PyGame [tutorial series][2]. To receive news regarding our latest tutorials and courses, you can subscribe to our [newsletter][3]. If this tutorial has been valuable, sharing this guide on social media would be highly appreciated.

 [1]: https://pygame.org
 [2]: https://learn.yorkcs.com/category/tutorials/gamedev/pygame/pygame-basics/
 [3]: https://learn.yorkcs.com/newsletter