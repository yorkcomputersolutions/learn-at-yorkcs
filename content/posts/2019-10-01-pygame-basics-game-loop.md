---
title: 'PyGame Basics: Game Loop'
author: Jared
type: post
date: 2019-10-01T17:47:31+00:00
url: /2019/10/01/pygame-basics-game-loop/
featured_image: /wp-content/uploads/2019/10/pygame-basics-game-loop.png
rank_math_primary_category:
  - 315
rank_math_description:
  - Learn what you need to know to add a basic game loop to your PyGame game. Delivered in a bite-sized chunk, we wrote this guide to help you out with PyGame.
rank_math_focus_keyword:
  - PyGame game loop
rank_math_robots:
  - 'a:1:{i:0;s:5:"index";}'
rank_math_internal_links_processed:
  - 1
rank_math_analytic_object_id:
  - 16
categories:
  - PyGame
series:
  - PyGame Basics
tags:
  - cross-platform
  - tutorial

---
In this tutorial, we will be creating the game loop of our [PyGame][1] game. By adding the game loop, we can keep our game window from disappearing. If by chance you don&#8217;t have a game window yet, you can check out [this part][2] of our [PyGame Basics][3] series.

To create our game loop, we need a clock to set the FPS, or frames-per-second of our game. Under the last line of our game window code, add the following line:

{{<highlight py3>}}
clock = pygame.time.Clock()
{{</highlight>}}

We will also need a variable to determine whether or not the game is running. Under the line where we instantiate a clock, add the following variable declaration:

{{<highlight py3>}}
running = True
{{</highlight>}}

Now we need to add the actual game loop. Our PyGame game loop will be made up of a while loop. Let&#8217;s start by adding a while loop checking if _running_ is true.

{{<highlight py3>}}
while running:
{{</highlight>}}

Inside our while loop, we need to check if any internal game events have been triggered. For example, if we click the close button, we want our game window to close. To add this mechanic, append the following bit inside our while loop.

{{<highlight py3>}}
for event in pygame.event.get():
    if event.type == pygame.QUIT:
        running = False
{{</highlight>}}

After the for loop, but still inside the while loop, we need to render anything that needs to be drawn, as well as ensure the game FPS is set at 60. Add the following two lines after the for loop.

{{<highlight py3>}}
pygame.display.update()
clock.tick(60)
{{</highlight>}}

Additionally, we will also want the game to quit properly if the game loop breaks. Add these two lines after the while loop.

{{<highlight py3>}}
pygame.quit()
quit()
{{</highlight>}}

When we run the game at this point, we should see that our game window no longer disappears. We are now ready to add some content to our game!

If you found this guide helpful, you may consider taking a look at the [rest of this tutorial series][3]. To receive news about our latest tutorials and courses, be sure to subscribe to our [newsletter][4].

Sharing this tutorial on your favorite social media platform would be much appreciated, only if you found this guide valuable.

 [1]: https://pygame.org
 [2]: https://learn.yorkcs.com/2019/10/01/pygame-basics-game-window/
 [3]: https://learn.yorkcs.com/category/tutorials/gamedev/pygame/pygame-basics/
 [4]: https://learn.yorkcs.com/newsletter