---
title: 'Phaser 3 Basics: Loading Images'
author: Jared
type: post
date: 2019-09-27T17:57:37+00:00
url: /2019/09/27/phaser-3-basics-loading-images/
featured_image: /wp-content/uploads/2019/09/loading-images-wp.png
rank_math_primary_category:
  - 297
rank_math_description:
  - Learn how to load images with Phaser 3.
rank_math_focus_keyword:
  - load images with Phaser 3
rank_math_robots:
  - 'a:1:{i:0;s:5:"index";}'
rank_math_internal_links_processed:
  - 1
rank_math_analytic_object_id:
  - 25
categories:
  - Phaser 3
series:
  - Phaser 3 Basics
tags:
  - gamedesign

---
In this guide, we will be taking a look at how to load images with Phaser 3. Hopefully you have a scene already setup. If you don&#8217;t have a scene setup already, please visit my tutorial on writing [boilerplate code][1].

In your scene, define a _preload_ function if you haven&#8217;t already. To define an image, the syntax is the following:

this.load.image(<key>, <path with extension>);

Actual code could look like so:

{{<highlight js>}}
this.load.image("myimage", "my-path/to-image/myimage.png");
{{</highlight>}}

In our method call, _key_ is the name you want to reference your image with in your code. The second argument should be the path to locate the image, and it should include the file extension.

Try loading an image. If you have a _create_ method in your scene, you can add an image referencing the key you defined. For example, to draw an image at x: 0 and y: 0, which is the corner of the screen, you can write:

{{<highlight js>}}
this.add.image(0, 0, "myimage");
{{</highlight>}}

Of course, you can assign the return value of the method call to a variable or property like this:

{{<highlight js>}}
this.myImage = this.add.image(0, 0, "myimage");
{{</highlight>}}

With that, you now know how to load and draw a basic image with Phaser 3! If you found this guide helpful, you can find other tutorials in this series [here][2]. The goal of these articles is to provide you with basic information on learning Phaser without having to follow the steps in any specific order. If you like the series so far, and would like to receive news on my future tutorials and courses, please fill out the [form][3]. Sharing this guide on social media would also be much appreciated if you found this guide valuable.

 [1]: https://learn.yorkcs.com/2019/09/27/phaser-3-basics-boilerplate-code/
 [2]: https://learn.yorkcs.com/category/tutorials/gamedev/phaser-3/phaser-3-basics/
 [3]: https://yorkcs.activehosted.com/f/1