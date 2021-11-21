---
title: 'PyGame Basics: Mouse Input'
author: Jared
type: post
date: 2019-10-03T23:05:10+00:00
url: /2019/10/03/pygame-basics-mouse-input/
featured_image: /wp-content/uploads/2019/10/pygame-basics-mouse-input.png
rank_math_primary_category:
  - 315
rank_math_description:
  - Learn how to capture and utilize mouse input with PyGame! This bite-sized guide shows you everything you need to start adding input to your games.
rank_math_focus_keyword:
  - mouse input
rank_math_robots:
  - 'a:1:{i:0;s:5:"index";}'
rank_math_internal_links_processed:
  - 1
rank_math_analytic_object_id:
  - 13
categories:
  - PyGame
series:
  - PyGame Basics
tags:
  - PyGame

---
In this guide, we will be taking a look at how to utilize mouse input with [PyGame][1].

## Mouse Position

To retrieve the position of the mouse, you can use the following line:

{{<highlight py3>}}
mousex, mousey = pygame.mouse.get_pos()
{{</highlight>}}

Of course, with the above line, you can access the x position of the mouse with _mousex_, and the y position of the mouse with _mousey_. Ensure this line is executed within the game loop, either in a dedicated update function, or directly within the loop.

## Mouse Clicks

Mouse clicks can be listened to by capturing the _pygame.MOUSEBUTTONUP_ event. Let&#8217;s try this. In your update function/game loop, add the following code:

{{<highlight py3>}}
for event in pygame.event.get():
    if event.type == pygame.MOUSEBUTTONUP:
        print("Mouse click detected.")
{{</highlight>}}

However, what if you want to distinguish which mouse button you clicked? You can use the _event.button_ property to determine which mouse button was clicked. Here is a list of possible integers _event.button_ can be:

<table class="wp-block-table">
  <tr>
    <td>
      Integer
    </td>
    
    <td>
      Mouse Button
    </td>
  </tr>
  
  <tr>
    <td>
      1
    </td>
    
    <td>
      left click
    </td>
  </tr>
  
  <tr>
    <td>
      2
    </td>
    
    <td>
      middle click
    </td>
  </tr>
  
  <tr>
    <td>
      3
    </td>
    
    <td>
      right click
    </td>
  </tr>
  
  <tr>
    <td>
      4
    </td>
    
    <td>
      scroll up
    </td>
  </tr>
  
  <tr>
    <td>
      5
    </td>
    
    <td>
      scroll down
    </td>
  </tr>
</table>

For example, to detect mouse right clicks, you could add the following inside your _pygame.MOUSEBUTTONUP_ if statement:

{{<highlight py3>}}
if event.button == 3:
    print("Right mouse button clicked")
{{</highlight>}}

If you wanted to check if the user is scrolling up, you can add the following code:

{{<highlight py3>}}
if event.type == pygame.MOUSEBUTTONDOWN:
    if event.button == 4:
        print("Scrolling up")
{{</highlight>}}

To scroll up, you can check if _event.button_ is equal to five.

{{<highlight py3>}}
if event.button == 5:
    print("Scrolling down")
{{</highlight>}}

## Concluding Thoughts

Hopefully you have found this guide helpful. Mouse input can be extremely useful for adding interaction to your [PyGame][1]. If you would like to check out the rest of this series, you take a look at it [here][2]. To receive news regarding our latest tutorials and courses, you can subscribe to our [newsletter][3] here. Sharing this tutorial on your favorite social media platform would also be much appreciated, of course only if you found this guide useful.

 [1]: https://pygame.org
 [2]: https://learn.yorkcs.com/category/tutorials/gamedev/pygame/pygame-basics/
 [3]: https://learn.yorkcs.com/newsletter