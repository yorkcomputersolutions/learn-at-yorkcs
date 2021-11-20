---
title: 'PyGame Basics: Image Effects'
author: Jared
type: post
date: 2019-10-03T21:07:41+00:00
url: /2019/10/03/pygame-basics-image-effects/
featured_image: /wp-content/uploads/2019/10/image-effects.png
enclosure:
  - |
    |
        https://learn.yorkcs.com/wp-content/uploads/2019/10/image-effects.mp4
        842011
        video/mp4
        
rank_math_primary_category:
  - 315
rank_math_description:
  - Learn the different image effects you can apply within our PyGame game. Get started with this bite-sized guide, and start builing the game of your dreams.
rank_math_focus_keyword:
  - image effects
rank_math_robots:
  - 'a:1:{i:0;s:5:"index";}'
rank_math_internal_links_processed:
  - 1
rank_math_analytic_object_id:
  - 14
categories:
  - PyGame
series:
  - PyGame Basics
tags:
  - free
  - guide
  - PyGame
  - Python
  - tutorial

---
In this guide, we will be taking a look at some different image effects you can use within your [PyGame][1]. In the examples below, I will be drawing sample images at x: 480 and y: 128. To learn how to position images, you can take a look at [this guide][2] of ours.

## Scaling Images

You can scale images with PyGame using the _pygame.transform.scale_ method. This method, like the other methods part of _pygame.transform_. For example, you can write:

<pre class="EnlighterJSRAW" data-enlighter-language="python" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">scaled_myimage = pygame.transform.scale(myimage, (128, 480))</pre>

With the _pygame.transform.scale_ method, the first argument is the image, and the second argument is a tuple representing the new size of the image.<figure class="wp-block-image">

<img src="https://learn.yorkcs.com/wp-content/uploads/2019/10/Screenshot_20191002_140310-700x551.png" alt="" class="wp-image-7934" /> </figure> 

## Flipping Images

To flip an image with PyGame, we can use the _pygame.transform.flip_ method. The first argument is the image you want to draw, the second is a boolean determining whether to flip the image horizontally, and the third is a boolean determining whether the image should be flipped vertically.

To flip an image horizontally, we could use the following line:

<pre class="EnlighterJSRAW" data-enlighter-language="python" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">flipped_myimage = pygame.transform.flip(myimage, True, False)</pre><figure class="wp-block-image">

<img src="https://learn.yorkcs.com/wp-content/uploads/2019/10/Screenshot_20191002_141153-700x551.png" alt="" class="wp-image-7937" /> </figure> 

Likewise, to flip an image vertically, we can write this line:

<pre class="EnlighterJSRAW" data-enlighter-language="python" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">flipped_myimage = pygame.transform.flip(myimage, False, True)</pre><figure class="wp-block-image">

<img src="https://learn.yorkcs.com/wp-content/uploads/2019/10/Screenshot_20191002_141646-700x551.png" alt="" class="wp-image-7941" /> </figure> 

Of course, to flip an image horizontally and vertically, you can set the second and third arguments to true.

<pre class="EnlighterJSRAW" data-enlighter-language="python" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">flipped_myimage = pygame.transform.flip(myimage, True, True)</pre><figure class="wp-block-image">

<img src="https://learn.yorkcs.com/wp-content/uploads/2019/10/Screenshot_20191002_141531-700x552.png" alt="" class="wp-image-7940" /> </figure> 

## Rotating Images

To rotate images, we can use the _pygame.transform.rotate_ method.

<pre class="EnlighterJSRAW" data-enlighter-language="python" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">rotated_myimage = pygame.transform.rotate(myimage, 45)</pre><figure class="wp-block-image">

<img src="https://learn.yorkcs.com/wp-content/uploads/2019/10/Screenshot_20191002_143126-700x554.png" alt="" class="wp-image-7946" /> </figure> 

Now, if you were to update the angle every tick, you will notice the origin is not centered. To center the origin of the image, you can add the following function. This function was originally taken from the [PyGame Wiki][3].

<pre class="EnlighterJSRAW" data-enlighter-language="python" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">def rot_center(image, angle):
    orig_rect = image.get_rect()
    rot_image = pygame.transform.rotate(image, angle)
    rot_rect = orig_rect.copy()
    rot_rect.center = rot_image.get_rect().center
    rot_image = rot_image.subsurface(rot_rect).copy()
    return rot_image</pre>

I think this solution is much better than anything I could come up with, which is why I recommend the solution on the [PyGame Wiki][3].

To utilize this in your game, you could add the following to your game loop/draw function:

<pre class="EnlighterJSRAW" data-enlighter-language="python" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">rotated_image = rot_center(myimage, angle)
display.blit(image, image.get_rect())</pre><figure class="wp-block-video"><video autoplay loop muted src="https://learn.yorkcs.com/wp-content/uploads/2019/10/image-effects.mp4"></video><figcaption>Now the image is rotating around the center! Fantastic.</figcaption></figure> 

## Rotating and Scaling Images

You can also combine rotate and scale operations with a single method:

<pre class="EnlighterJSRAW" data-enlighter-language="python" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">image = pygame.transform.rotozoom(myimage, 45, 0.5)</pre>

With the _rotozoom_ method, the first argument is the surface (image), the second is the degrees to rotate the surface, and the last argument is the new scale.

If I wanted to rotate an image 45 degrees, and scale it 50% smaller, you could write the following line:

<pre class="EnlighterJSRAW" data-enlighter-language="python" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">image = pygame.transform.rotozoom(myimage, 45, 2)</pre>

Then I would end up with the final result:<figure class="wp-block-image">

<img src="https://learn.yorkcs.com/wp-content/uploads/2019/10/Screenshot_20191003_134236-700x551.png" alt="" class="wp-image-8001" /> </figure> 

## Double the Scale of an Image

Another interesting image effect we can use is the _pygame.transform.scale2x_ method. This method doubles the scale of a surface. We just simply pass in an image, then it returns the new surface (the image twice the size.)

<pre class="EnlighterJSRAW" data-enlighter-language="python" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">image = pygame.transform.scale2x(myimage)</pre>

Obviously, we can blit this new surface.<figure class="wp-block-image">

<img src="https://learn.yorkcs.com/wp-content/uploads/2019/10/Screenshot_20191003_135025-700x549.png" alt="" class="wp-image-8003" /> </figure> 

## Concluding Thoughts

Hopefully this guide has helped you figure out some of the different image effects you can use with PyGame. Keep in mind, when I mentioned images in this tutorial, I really meant surfaces. You can find other guides in this series [here][4]. To learn about new tutorials and guides we release, you can subscribe to our [newsletter][5]. Sharing this guide on your social media platform of choice would also be much appreciated.

 [1]: https://pygame.org
 [2]: https://learn.yorkcs.com/2019/10/02/pygame-basics-drawing-images/
 [3]: https://www.pygame.org/wiki/RotateCenter?parent=CookBook
 [4]: https://learn.yorkcs.com/category/tutorials/gamedev/pygame/pygame-basics/
 [5]: https://learn.yorkcs.com/newsletter