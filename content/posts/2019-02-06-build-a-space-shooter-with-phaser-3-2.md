---
title: Build a Space Shooter with Phaser 3 – 2
author: Jared
type: post
date: 2019-02-06T13:54:57+00:00
url: /2019/02/06/build-a-space-shooter-with-phaser-3-2/
featured_image: /wp-content/uploads/2019/02/thumbnail_wp_part2.jpg
rank_math_seo_score:
  - 70
rank_math_facebook_enable_image_overlay:
  - off
rank_math_facebook_image_overlay:
  - play
rank_math_twitter_use_facebook:
  - on
rank_math_twitter_card_type:
  - summary_large_image
rank_math_twitter_enable_image_overlay:
  - off
rank_math_twitter_image_overlay:
  - play
rank_math_internal_links_processed:
  - 1
rank_math_focus_keyword:
  - phaser
rank_math_rich_snippet:
  - article
rank_math_snippet_article_type:
  - BlogPosting
rank_math_snippet_book_editions:
  - 'a:1:{i:0;a:1:{s:11:"book_format";s:9:"Hardcover";}}'
rank_math_snippet_event_type:
  - Event
rank_math_snippet_jobposting_unpublish:
  - on
rank_math_snippet_music_type:
  - MusicGroup
rank_math_snippet_product_instock:
  - on
rank_math_snippet_recipe_instruction_type:
  - SingleField
rank_math_snippet_review_worst_rating:
  - 1
rank_math_snippet_review_best_rating:
  - 5
rank_math_snippet_review_location:
  - bottom
rank_math_snippet_review_shortcode:
  - '[rank_math_review_snippet]'
rank_math_robots:
  - 'a:1:{i:0;s:5:"index";}'
rank_math_schema_Article:
  - 'a:6:{s:5:"@type";s:11:"BlogPosting";s:8:"headline";s:11:"%seo_title%";s:13:"datePublished";s:20:"%date(Y-m-dTH:i:sP)%";s:12:"dateModified";s:24:"%modified(Y-m-dTH:i:sP)%";s:6:"author";a:2:{s:5:"@type";s:6:"Person";s:4:"name";s:5:"Jared";}s:8:"metadata";a:3:{s:5:"title";s:7:"Article";s:9:"isPrimary";b:1;s:4:"type";s:8:"template";}}'
rank_math_analytic_object_id:
  - 76
categories:
  - Phaser 3
series:
  - Build a Space Shooter with Phaser 3
tags:
  - game dev
  - phaser
  - phaser3

---
In the last part of this course, we finished creating the files and folders we need for our game. The next thing we need to do is start building out our `index.html`. In order to start coding our HTML and JavaScript files, you will need a text editor. If you have not programmed yet, any text editor will work such as Notepad, Visual Studio Code, Atom, etc. I personally use Visual Studio Code for web development, it&#8217;s fast and simply works.

To start, open your `index.html` file and type the following:

<pre class="EnlighterJSRAW" data-enlighter-language="html" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">&lt;!DOCTYPE html>
&lt;html>
  &lt;head>
    &lt;meta charset="utf-8">
    &lt;meta lang="en-us">
    &lt;title>Space Shooter&lt;/title>
    &lt;script src="js/phaser.js">&lt;/script> &lt;!-- the file name should be the same as the Phaser script you added. -->
  &lt;/head>

  &lt;body>
    &lt;script src="js/SceneMainMenu.js">&lt;/script>
    &lt;script src="js/SceneMain.js">&lt;/script>
    &lt;script src="js/SceneGameOver.js">&lt;/script>
    &lt;script src="js/game.js">&lt;/script>
  &lt;/body>
&lt;/html></pre>

In this last snippet, we declare the file to be an HTML file (hence the .html file extension), and declare the scripts we will use. Note the order we declare the scripts that contain &#8220;Scene&#8221; in them in comparison to the `game.js` script. The order is very important because JavaScript is interpreted from top to bottom. We will be referencing code from our three scene scripts in `game.js`.

Next, we will need to initialize our Phaser game inside game.js. Take a moment and open up game.js if you haven&#8217;t already and create a JavaScript object like the following:

<pre class="EnlighterJSRAW" data-enlighter-language="js" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="1" data-enlighter-title="" data-enlighter-group="">var config = {

};</pre>

This JavaScript object will contain the configuration properties that we will feed our upcoming Phaser game instance. Inside our config object add:

<pre class="EnlighterJSRAW" data-enlighter-language="js" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="2" data-enlighter-title="" data-enlighter-group="">type: Phaser.WEBGL,
  width: 480,
  height: 640,
  backgroundColor: "black",
  physics: {
    default: "arcade",
    arcade: {
      gravity: { x: 0, y: 0 }
    }
  },
  scene: [],
  pixelArt: true,
  roundPixels: true</pre>

So far inside our configuration object we are telling Phaser that we want to ensure our game is being rendered via WebGL instead of using ordinary Canvas rendering tech. The next part of the config includes `width` and `height` which define the size of our game on the page. The property `backgroundColor` defines the background color that will be shown behind our game. The next property, `physics` defines the default physics engine that we will be using, which is `arcade`. Arcade physics work well when we want basic collision detection without many bells and whistles. Inside the `physics` property, we also set default gravity of our physics world. The next property, `scene` is set to an array which we will add to in a bit. Finally we want Phaser to ensure pixels are crisp just like the great nostalgic video games we&#8217;ve come to know and love.

The scene array that we have defined inside our config object is needed in order to declare the order of our scenes in our game. A scene is effectively like any sort of &#8220;screen&#8221; you see in a video game. For example, the main menu, the play state, and the game over screen are what I call separate &#8220;screens&#8221;. Well, a scene is pretty much the same as a screen. We will define our scenes as a JavaScript class (a class is still an object, the syntax is just different and helps us organize our code better.) Now we will define our scene classes inside the array of the scene property we just wrote:

<pre class="EnlighterJSRAW" data-enlighter-language="js" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="11" data-enlighter-title="" data-enlighter-group="">},
  scene: [
    SceneMainMenu,
    SceneMain,
    SceneGameOver
  ],
  pixelArt: true,</pre>

We are now finished with our configuration object! We will not need to touch it for the duration of this course. The final line of code we need (and arguably most important) after the last curly brace of our config object is:

<pre class="EnlighterJSRAW" data-enlighter-language="js" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="21" data-enlighter-title="" data-enlighter-group="">var game = new Phaser.Game(config);</pre>

And there we have it! Our `game.js` file is complete. Now we need to define a class for each of our scene scripts. Lets open `SceneMainMenu.js` first and add the following:

<pre class="EnlighterJSRAW" data-enlighter-language="js" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">class SceneMainMenu extends Phaser.Scene {
  constructor() {
    super({ key: "SceneMainMenu" });
  }

  create() {
    this.scene.start("SceneMain");
  }
}</pre>

Here we are declaring a class with `class SceneMainMenu`. On the same line we added `extends Phaser.Scene {`. Extending `Phaser.Scene` means to build on top of Phaser&#8217;s Scene class (`Phaser.Scene` means a class named `Scene` which is a property of the object `Phaser`.) Inside the class we have just declared, there are two functions: `constructor` and `create`. The `constructor` function is called immediately when instantiating (creating an instance) the class. Within the constructor we have:

<pre class="EnlighterJSRAW" data-enlighter-language="js" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="3" data-enlighter-title="" data-enlighter-group="">super({ key: "SceneMainMenu" });</pre>

which is effectively the same (technically speaking) as:

<pre class="EnlighterJSRAW" data-enlighter-language="js" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="false" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">var someScene = new Phaser.Scene({ key: "SceneMainMenu" });</pre>

Instead of creating an instance of `Phaser.Scene` and assigning it to a variable, we are instead defining our scene as a class that we can assign a custom `preload`, `create`, and eventually an `update` function. This is what I mean when I say build on top of the existing `Phaser.Scene` class. The `create` function within our `SceneMainMenu` class will be called as soon as the scene is started. Inside our `create` function we included:

<pre class="EnlighterJSRAW" data-enlighter-language="js" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="7" data-enlighter-title="" data-enlighter-group="">this.scene.start("SceneMain");</pre>

The plan is to redirect the player to the main play scene, where all the action is. I think it would be better to start on the game play and work backwards to the main menu. Who wants to work on those boring buttons and interface elements anyway? Especially when we can instead code something much more exciting&#8230; <del>for now&#8230;</del> right? 🙂

We can finish up by the code we just typed for `SceneMainMenu` into `SceneMain.js` and `SceneGameOver.js`. Below is what you should end up with for all three scripts:

<pre class="EnlighterJSRAW" data-enlighter-language="js" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="SceneMainMenu.js" data-enlighter-group="">class SceneMainMenu extends Phaser.Scene {
  constructor() {
    super({ key: "SceneMainMenu" });
  }

  create() {
    this.scene.start("SceneMain");
  }
}</pre>

<pre class="EnlighterJSRAW" data-enlighter-language="js" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="SceneMain.js" data-enlighter-group="">class SceneMain extends Phaser.Scene {
  constructor() {
    super({ key: "SceneMain" });
  }

  create() {
    
  }
}</pre>

<pre class="EnlighterJSRAW" data-enlighter-language="js" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="SceneGameOver.js" data-enlighter-group="">class SceneGameOver extends Phaser.Scene {
  constructor() {
    super({ key: "SceneGameOver" });
  }

  create() {
    
  }
}</pre>

If you have questions or suggestions, feel free to leave a comment below and I&#8217;ll be happy to help you out! If you would like to receive updates on new courses I release via email, feel free to fill out the [form][1].

 [1]: https://docs.google.com/forms/d/e/1FAIpQLSfSAg6xMDrk44pbmIlVUqLwjm9FHaKPdy_WcbHUmLWWyXMQag/viewform