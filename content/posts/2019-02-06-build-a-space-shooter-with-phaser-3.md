---
title: Build a Space Shooter with Phaser 3 – 1
author: Jared
type: post
date: 2019-02-06T11:14:32+00:00
url: /2019/02/06/build-a-space-shooter-with-phaser-3/
featured_image: /wp-content/uploads/2019/02/thumbnail_wp_part1-1.jpg
rank_math_seo_score:
  - 84
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
  - 77
categories:
  - Phaser 3
series:
  - Build a Space Shooter with Phaser 3
tags:
  - game dev
  - phaser
  - phaser3

---
With the latest release of Phaser 3 (as of now, v3.16.1), there has never been a better time to jump into Phaser than now! In this free course, we will be exploring creating a basic space shooter with Phaser 3. I will start by saying that it is quite beneficial to have the basics of JavaScript under your belt. If you don&#8217;t, be sure to check out my free course, &#8220;[JavaScript Beginner Blocks][1]&#8220;. That course will cover everything in JavaScript you need to know to start this one. However, no matter if you have never used Phaser before, or just dabbled in it for a little bit, this course is for you. By the end of this course, you should have adequate knowledge to start building games of your own with Phaser 3. You can check out Phaser at the official [website][2].

Concepts you will learn about:  


  * Basics of JavaScript ES6 classes
  * Drawing sprites
  * Scaling and rotating sprites
  * Playing sounds
  * Changing scenes

### Ensure a Web Server is Set Up

Even though Phaser games are ran in your browser, you unfortunately can&#8217;t just run a local HTML file directly from your file system. When requesting files over http, the security of the server allows you to access only the files you&#8217;re allowed to. When loading a file from the local file system (the file:// protocol), your browser highly restricts it for obvious security reasons. It&#8217;s no good to allow code on a website to read anything in your raw file system. Because of this, we will need to host our game on a local web server.

We recommend checking out Phaser&#8217;s official guide, &#8220;<a rel="noreferrer noopener" aria-label="Getting Started with Phaser 3 (opens in a new tab)" href="https://phaser.io/tutorials/getting-started-phaser3/part2" target="_blank">Getting Started with Phaser 3</a>&#8220;, to learn which web server is compatible with your system and there are links to each one. The guide also provides some detailed summaries on the each of the various web servers mentioned.

### Create the Files and Folders Needed

First, find the location where your web server hosts files from (WAMP Server, for example, hosts files from the www directory within it&#8217;s installation folder at C:/wamp64.) Once you have found the location, create a new folder inside it and call it anything you want.

Next, enter the folder and create a new file called, &#8220;index.html&#8221;. Our index file is where we will declare the location of our Phaser script and the rest of our game scripts.

Now we will need to create two new folders, I called the first one `content` for our game content (sprites, audio, etc.), and the other one, `js`, which will contain our Phaser script and our other game scripts. Feel free to name these two folders anything you would like, after all, it is your game. One of the folders just needs to be dedicated to the content for our game, and the other for the JavaScript files. Since we have our folder for content and JavaScript, create four new files inside the newly created folder for JavaScript called: `SceneMainMenu.js`, `SceneMain.js`, `SceneGameOver.js`, and `game.js`. I will explain what those files will do shortly, but next we need to populate our content folder with the content for our game. After all, what&#8217;s the point of a game if there&#8217;s nothing to see? 🙂

So far, the file structure we have created should look like:

<pre class="wp-block-preformatted">(game folder)<br />|_ index.html<br />|_ content/<br />|_ js/<br />   |_ game.js<br />   |_ SceneGameOver.js<br />   |_ SceneMain.js<br />   |_ SceneMainMenu.js<br /></pre>

Now to add content to our game, we will first need content. I have prepared some assets for this course that you can download for free <a href="http://www.mediafire.com/file/gsymlxluw1eve8n/P3SpaceShooterContent.zip/file" target="_blank" rel="noreferrer noopener" aria-label=" (opens in a new tab)">here</a>. Otherwise, you create your own assets if you wish. Keep in mind that if you create your own assets, Phaser requires frames to be in a horizontal row on the images with animations. Below is a list of the content we will need:

#### Content needed:

  * **Sprites (images)** 
      * sprBtnPlay.png (the play button)
      * sprBtnPlayHover.png (the play button when mouse is over)
      * sprBtnPlayDown.png (the play button when clicked)
      * sprBtnRestart.png (the restart button)
      * sprBtnRestartHover.png (the restart button on mouse over)
      * sprBtnRestartDown (the restart button when clicked)
      * sprBg0.png (a background layer of stars with transparency around the stars)
      * sprBg1.png (another background layer of stars with transparency around the stars)
      * sprEnemy0.png (the first enemy, this is an animation)
      * sprEnemy1.png (the second enemy, this is not an animation)
      * sprEnemy2.png (the third enemy, this is an animation)
      * sprLaserEnemy.png (laser shot by enemies)
      * sprLaserPlayer.png (laser shot by the player)
      * sprExplosion.png (an explosion animation)
      * sprPlayer.png (the player, this is an animation) 
  * **Audio (.wav files)** 
      * sndExplode0.wav (the first explosion sound)
      * sndExplode1.wav (the second explosion sound)
      * sndLaser.wav (the sound of a laser being shot)
      * sndBtnOver.wav (the sound of mouse moving over button)
      * sndBtnDown.wav (the sound of button when clicked) 

Once you downloaded the assets (or made your own), we will move those files into the content directory we have made.

Finally, we need to download the latest Phaser script. One method of acquiring this (there are multiple), is to head over to GitHub (specifically <a rel="noreferrer noopener" aria-label="here (opens in a new tab)" href="https://github.com/photonstorm/phaser/tree/master/dist" target="_blank">here</a>). You will want either `phaser.js` or `phaser.min.js`. The file `phaser.js` contains the source code for Phaser in a readable form, which is useful if you wanted to contribute to Phaser, or to understand how something is implemented under-the-hood. The other file, `phaser.min.js` is meant for distribution, and is compressed to reduce file size. For our purposes, it won&#8217;t really matter which one we download, so decide which and click the appropriate link. You will then be greeted by a page that displays a &#8220;View raw&#8221; button near the center of the page and roughly halfway down. Next, click the &#8220;View raw&#8221; link, right click anywhere on the page that appears, then click &#8220;Save Page As&#8221;. A save dialog will appear where you should save the Phaser file in the JavaScript directory we created earlier.

With that, we will wrap up the first part of our free course, &#8220;Build a Space Shooter with Phaser 3&#8221;.

If you would like to receive updates on new courses I release via email, feel free to fill out the [form][3].

 [1]: https://learn.yorkcs.com/product/javascript-beginner-blocks/
 [2]: https://phaser.io/
 [3]: https://docs.google.com/forms/d/e/1FAIpQLSfSAg6xMDrk44pbmIlVUqLwjm9FHaKPdy_WcbHUmLWWyXMQag/viewform