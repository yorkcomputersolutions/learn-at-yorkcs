---
title: 'Phaser 3 Basics: Changing Positions'
author: Jared
type: post
date: 2019-09-28T19:39:44+00:00
url: /2019/09/28/phaser-3-basics-changing-positions/
featured_image: /wp-content/uploads/2019/09/changing-positions-wp.png
rank_math_primary_category:
  - 297
rank_math_description:
  - "If you're learning Phaser 3, learning how to change the position of images and sprites can be incredibly useful. Luckily, this guide shows you how."
rank_math_focus_keyword:
  - change the position
rank_math_robots:
  - 'a:1:{i:0;s:5:"index";}'
rank_math_internal_links_processed:
  - 1
rank_math_analytic_object_id:
  - 21
categories:
  - Phaser 3
series:
  - Phaser 3 Basics
tags:
  - gamedev
  - phaser
  - Phaser 3

---

In this guide, we will be taking a look at how to manipulate the position of images and sprites in [Phaser 3][1]. Being able to change the x and y positions of objects in your game is very useful and will allow you to add some awesome mechanics. Before we begin, I will assume you already created a scene and added a sprite or image. Don&#8217;t have a scene added? I would recommend checking out [this tutorial][2] I wrote. If you have no images or sprites yet, and you need to learn how to add them, check out this [guide][3].

If you haven&#8217;t assigned the return value of the _add.sprite_ method yet, this will be necessary. For example, change this:

<pre class="EnlighterJSRAW" data-enlighter-language="js" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">this.add.sprite(128, 128, "myimage");</pre>

To:

<pre class="EnlighterJSRAW" data-enlighter-language="js" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">this.myImage = this.add.sprite(128, 128, "myimage");</pre>

At this point, we can change the position of our image or sprite. There are a few ways of accomplishing this. There are a few methods to set position. Alternatively, you can directly set the x and y positions of a sprite or image.

## Setting Positions via Methods

One way to set the position of a sprite or image is using the _setPosition_ method. Normally, it&#8217;s common to enter the new x and y position as arguments like so:

<pre class="EnlighterJSRAW" data-enlighter-language="js" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">this.myImage.setPosition(128, 256);</pre>

You can also set the position of a sprite or image on specific axes.

To set the x position of a sprite or image via a method, you can write:

<pre class="EnlighterJSRAW" data-enlighter-language="js" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">this.myImage.setX(320);</pre>

To add, if you want to set the y position of a sprite or image via methods, you can add:

<pre class="EnlighterJSRAW" data-enlighter-language="js" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">this.myImage.setY(240);</pre>

## Setting Positions Directly

You can also set the x and y positions of a sprite or image without methods by directly setting the properties. I probably wouldn&#8217;t recommend changing positions this way (though I occasionally do), but you can type:

<pre class="EnlighterJSRAW" data-enlighter-language="js" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">this.myImage.x = 280;</pre>

Of course, since you&#8217;re setting properties, you can increment the values as well like so:

<pre class="EnlighterJSRAW" data-enlighter-language="js" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">this.myImage.x += 32;</pre>

The same concept applies to setting the y position directly. For example, you could write:

<pre class="EnlighterJSRAW" data-enlighter-language="js" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">this.myImage.y = 48;</pre>

To increment the y position, you can also simply write:

<pre class="EnlighterJSRAW" data-enlighter-language="js" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">this.myImage.y += 32;</pre>

Hopefully this guide helped you out. You may want to consider taking a look at the other tutorials in this [series][4], if you liked this tutorial. If you would like to receive news of our future tutorials and courses, you can subscribe to our newsletter [here][5]. If you found this guide valuable, sharing this guide on your favorite social media would be highly appreciated as well. Stay tuned for more parts in this series.

 [1]: https://phaser.io
 [2]: https://learn.yorkcs.com/2019/09/27/phaser-3-basics-boilerplate-code/
 [3]: https://learn.yorkcs.com/2019/09/27/phaser-3-basics-loading-images/
 [4]: https://learn.yorkcs.com/category/tutorials/
 [5]: https://yorkcs.activehosted.com/f/1