---
title: 'PyGame Basics: Drawing Images'
author: Jared
type: post
date: 2019-10-02T17:47:36+00:00
url: /2019/10/02/pygame-basics-drawing-images/
featured_image: /wp-content/uploads/2019/10/pygame-basics-drawing-images.png
rank_math_primary_category:
  - 315
rank_math_description:
  - Learn how to draw images with PyGame! This bite-sized guide shows you how to draw images so you can build the game of your dreams.
rank_math_focus_keyword:
  - draw images with pygame
rank_math_robots:
  - 'a:1:{i:0;s:5:"index";}'
rank_math_internal_links_processed:
  - 1
rank_math_analytic_object_id:
  - 15
categories:
  - PyGame
series:
  - PyGame Basics
tags:
  - cross-platform
  - free
  - gamedesign
  - PyGame
  - Python

---
In this tutorial, we will be walking through how to draw images with [PyGame][1]. Let&#8217;s dive right in.

In your game file, you should see the _set_mode_ method being called. This method call returns a _Surface_, which is pretty much just the canvas that we&#8217;re drawing to. Make sure that the return value of this method call is being assigned to a variable. I named my variable, _display_ like to so:

{{<highlight py3>}}
display = pygame.display.set_mode((800, 600))
{{</highlight>}}

Next, we need to load an image. To do so, write this line before our game loop:

{{<highlight py3>}}
myimage = pygame.image.load("myimage.png")
{{</highlight>}}

At the bottom of our game loop, before the _display.update_ call (if you added one), add the following two lines:

{{<highlight py3>}}
display.fill((0, 0, 0))
display.blit(myimage, myimage.get_rect())
{{</highlight>}}

The first line fills the screen in black. It&#8217;s good practice to call this before our drawing code. Normally we only need to call this once. The _blit_ method is what actually copies our image to our surface, _display_, to be drawn. In this method, we are passing two arguments. The first argument we pass in is the image we want to draw. The second argument we&#8217;re passing is the source rectangle of the image. The source rectangle x and y positions are 0, 0 (top-left corner of image), the width and height is the width and height of the image. When we run our project, we should see the image we loaded display in the top-left corner of our game canvas.

![](https://learn.yorkcs.com/wp-content/uploads/2019/10/Screenshot_20191001_140604.png)

Alternatively, we can pass in x and y positions instead of a destination rectangle. To do so, adjust our blit call to:

{{<highlight py3>}}
display.blit(myimage, (480, 128))
{{</highlight>}}

When we run our game now we should see:

![](https://learn.yorkcs.com/wp-content/uploads/2019/10/Screenshot_20191002_133121.png)

Now you know how to draw images with [PyGame][1]! It&#8217;s not too bad once you practice adding more. Have questions? Please leave your questions and comments down below, and I will do my best to get back to you. If you found this guide useful, you may want to consider taking a look at the rest of our [Python Basics][2] tutorial series. To receive updates and news regarding our future tutorials and courses, you can subscribe to our [newsletter][3]. Sharing this guide on your favorite social media platform is also much appreciated, of course, only if you found this tutorial valuable.

 [1]: https://pygame.org
 [2]: https://learn.yorkcs.com/category/tutorials/gamedev/pygame/pygame-basics/
 [3]: https://learn.yorkcs.com/newsletter