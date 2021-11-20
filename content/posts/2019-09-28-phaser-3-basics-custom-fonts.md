---
title: 'Phaser 3 Basics: Custom Fonts'
author: Jared
type: post
date: 2019-09-28T19:33:01+00:00
url: /2019/09/28/phaser-3-basics-custom-fonts/
featured_image: /wp-content/uploads/2019/09/custom-fonts-wp.png
rank_math_primary_category:
  - 297
rank_math_description:
  - Learn how to load custom fonts with Phaser 3. This guide walks you through loading a font with CSS, making it usable with HTML, and then referencing it.
rank_math_focus_keyword:
  - custom fonts
rank_math_robots:
  - 'a:1:{i:0;s:5:"index";}'
rank_math_internal_links_processed:
  - 1
rank_math_analytic_object_id:
  - 23
categories:
  - Phaser 3
series:
  - Phaser 3 Basics
tags:
  - gamedesign
  - gamedev

---
In this guide, we will be covering how to load custom fonts, specifically TrueType fonts, with [Phaser 3][1]. To begin, you will need a scene setup for this guide. If you don’t have a scene made already, you can learn how to create one [here][2]. Essentially, you need to define a new font face with CSS, create a div utilizing the font to &#8220;load&#8221; it, and finally reference it within our game code.

If you have an external CSS file, you can add the following code there. If you have a pair of _<style>_ tags in the head of your _index.html_ file, you can also add this code there. Here is the styling code to add:

<pre class="EnlighterJSRAW" data-enlighter-language="css" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">@font-face {
    font-family: &lt;your font name here>;
    src: url('media/thefont.ttf');
    font-weight: 400;
    font-weight: normal;
}</pre>

Before you define your game scripts in the body, add the following div to &#8220;load&#8221; the font for use with Phaser.

<pre class="EnlighterJSRAW" data-enlighter-language="generic" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">&lt;div style="font-family:&lt;name of font you defined>; position: absolute; left:-1000px; visibility:hidden;">.&lt;/div></pre>

To use our custom font within our game, let&#8217;s try adding the following text object to the create method of our scene.

<pre class="EnlighterJSRAW" data-enlighter-language="css" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">this.add.text(128, 128, 'This is a test.', {
    fontFamily: '&lt;the font you defined>'
});</pre>

At this point, you should see the test text we wrote printed on the game screen in the custom font. With the right custom fonts, so much can be added to the character and atmosphere of the game.

If you found this guide valuable, be sure to check out the rest of the parts in this [tutorial series][3]. You can also subscribe to our [newsletter][4] to receive news about our latest tutorials and courses. Sharing this tutorial on your favorite social media platform is also much appreciated.

 [1]: https://phaser.io
 [2]: https://learn.yorkcs.com/2019/09/27/phaser-3-basics-boilerplate-code/
 [3]: https://learn.yorkcs.com/category/tutorials/gamedev/phaser-3/phaser-3-basics/
 [4]: https://yorkcs.activehosted.com/f/1