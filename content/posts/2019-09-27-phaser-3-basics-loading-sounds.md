---
title: 'Phaser 3 Basics: Loading Sounds'
author: Jared
type: post
date: 2019-09-27T19:21:34+00:00
url: /2019/09/27/phaser-3-basics-loading-sounds/
featured_image: /wp-content/uploads/2019/09/loading-sounds-wp.png
rank_math_primary_category:
  - 297
rank_math_description:
  - Learn how to load and play basic sounds with Phaser 3! This bite-sized guide will explain step-by-step each part of the process.
rank_math_focus_keyword:
  - Phaser 3
rank_math_robots:
  - 'a:1:{i:0;s:5:"index";}'
rank_math_internal_links_processed:
  - 1
rank_math_analytic_object_id:
  - 24
categories:
  - Phaser 3
series:
  - Phaser 3 Basics
tags:
  - loading sounds
  - phaser
  - Phaser 3
  - tutorial

---
In this guide, we will be learning how to load sounds with Phaser 3. At this point it would be useful if you had a scene already setup. If you don&#8217;t, you can take a look at my [boilerplate code][1] guide in this series.

In your scene, define a _preload_ method if you haven&#8217;t already. In order to define an image, you will need to follow this syntax:

this.load.audio(<key>, <path with extension>);

Realistically, this would look more like the following:

<pre class="EnlighterJSRAW" data-enlighter-language="js" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">this.load.audio("mysound", "my-path"/to-sound/mysound.m4a");</pre>

In this method call, _key_ is the name you wish to reference you sound within your code. The second argument should contain the path to your sound, including the file extension.

Try loading a sound by yourself. If you have a _create_ method in your scene, you can add a sound and reference the key you defined. We can use the _this.add.sound_ method and assign the returned sound to a variable or property.

<pre class="EnlighterJSRAW" data-enlighter-language="js" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">this.mySound = this.sound.add("mysound");</pre>

Whenever you want to play the sound within your code, ensure you&#8217;re calling the following method after the sound was defined above. Write the following line to play the sound:

<pre class="EnlighterJSRAW" data-enlighter-language="js" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">this.mySound.play();</pre>

With that, you now know how to play sounds with Phaser 3! If you found this guide valuable, you can find the rest of the articles in this series [here][2]. If you would like to receive news regarding future tutorials and courses we publish, you can subscribe to our newsletter [here][3]. You can also share this guide on social media, it really helps and is much appreciated; of course, only if you found this guide helpful.

 [1]: https://learn.yorkcs.com/2019/09/27/phaser-3-basics-boilerplate-code/
 [2]: https://learn.yorkcs.com/category/tutorials/gamedev/phaser-3/phaser-3-basics/
 [3]: https://yorkcs.activehosted.com/f/1