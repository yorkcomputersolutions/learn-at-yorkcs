---
title: 'PyGame Basics: Game Window'
author: Jared
type: post
date: 2019-10-01T17:22:57+00:00
url: /2019/10/01/pygame-basics-game-window/
featured_image: /wp-content/uploads/2019/10/pygame-basics-game-window.png
rank_math_primary_category:
  - 315
rank_math_description:
  - Learn how to setup a game window for your PyGame game. This guide shows you one of the components you need to start building the game of your dreams.
rank_math_focus_keyword:
  - PyGame game window
rank_math_robots:
  - 'a:1:{i:0;s:5:"index";}'
rank_math_internal_links_processed:
  - 1
rank_math_analytic_object_id:
  - 17
categories:
  - PyGame
series:
  - PyGame Basics
tags:
  - cross-platform
  - Python

---
In this guide, we will be creating the PyGame game window. If you don&#8217;t have a [PyGame][1] project setup yet, you can learn how to set one up [here][2]. In your main game file, you can add the following two lines to create our game window:

<pre class="EnlighterJSRAW" data-enlighter-language="python" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">display = pygame.display.set_mode((800, 600))
pygame.display.set_caption('My Window Title')</pre>

When you run the game, you should see a window appear for a couple seconds, then disappear. Take a look at [this part][3] of the series, where we add the game loop. After adding the game loop, your game window will no longer disappear.

Now you know how to create a PyGame game window! If you found this guide helpful, you may consider checking out the [rest of this series][4]. To receive news regarding our future tutorials and courses, you can subscribe to our [newsletter][5].

Sharing this guide on your favorite social media platform would be much appreciated, if you found this tutorial valuable.

 [1]: https://pygame.org
 [2]: https://learn.yorkcs.com/2019/10/01/pygame-basics-setting-up/
 [3]: https://learn.yorkcs.com/2019/10/01/pygame-basics-game-loop/
 [4]: https://learn.yorkcs.com/category/tutorials/gamedev/pygame/pygame-basics/
 [5]: https://learn.yorkcs.com/newsletter