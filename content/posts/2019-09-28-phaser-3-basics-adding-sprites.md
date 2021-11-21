---
title: 'Phaser 3 Basics: Adding Sprites'
author: Jared
type: post
date: 2019-09-28T19:35:52+00:00
url: /2019/09/28/phaser-3-basics-adding-sprites/
featured_image: /wp-content/uploads/2019/09/adding-sprites-wp.png
rank_math_primary_category:
  - 297
rank_math_focus_keyword:
  - adding sprites
rank_math_robots:
  - 'a:1:{i:0;s:5:"index";}'
rank_math_internal_links_processed:
  - 1
rank_math_analytic_object_id:
  - 22
categories:
  - Phaser 3
series:
  - Phaser 3 Basics

---
In the game development world, sprites are the 2D images in your game. Since this is the case, being able to add sprites is a very important skill to know. To begin, I will assume you have a scene already setup. If you don&#8217;t, feel free to check out [this guide][1] of mine to get you up to speed. We will also need an image loaded. If you&#8217;re new to loading images, you can check out [this tutorial][2] to learn that.

In the create method of your scene, you can add a sprite to your game with the following syntax:

this.add.sprite(<x>, <y>, <key>);

In the example above, the key is the image key you defined in the _preload_ method. Feel free to write the following code and change the image key to the one you defined.

{{<highlight js>}}
this.add.sprite(128, 128, "myimage");
{{</highlight>}}

If we run our game in the browser, we should see something like the following with the image of your choice.<figure class="wp-block-image">

<img loading="lazy" width="647" height="638" src="https://learn.yorkcs.com/wp-content/uploads/2019/09/phaser-3-basics-sprite.png" alt="" class="wp-image-7662" /> </figure> 

Hopefully this guide has been useful for you. If it has, you may be interested in checking out the rest of this [series][3]. If you would like to receive news of our latest tutorials and courses, be sure to fill out the [form][4]. Sharing this guide on your social media platform would also be much appreciated. Stay tuned for more parts to this series.

 [1]: https://learn.yorkcs.com/2019/09/27/phaser-3-basics-boilerplate-code/
 [2]: https://learn.yorkcs.com/2019/09/27/phaser-3-basics-loading-images/
 [3]: https://learn.yorkcs.com/category/tutorials/gamedev/phaser-3/phaser-3-basics/
 [4]: https://yorkcs.activehosted.com/f/1