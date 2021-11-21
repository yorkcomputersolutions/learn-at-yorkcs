---
title: Build a Space Shooter with Phaser 3 – 5
author: Jared
type: post
date: 2019-02-08T13:26:46+00:00
url: /2019/02/08/build-a-space-shooter-with-phaser-3-5/
featured_image: /wp-content/uploads/2019/02/thumbnail_wp_part5.jpg
rank_math_internal_links_processed:
  - 1
rank_math_primary_category:
  - 119
rank_math_seo_score:
  - 79
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
rank_math_focus_keyword:
  - phaser
rank_math_robots:
  - 'a:1:{i:0;s:5:"index";}'
rank_math_snippet_shortcode:
  - '[rank_math_rich_snippet]'
rank_math_snippet_course_provider_type:
  - Organization
rank_math_snippet_event_performer_type:
  - Person
rank_math_schema_Article:
  - 'a:6:{s:5:"@type";s:11:"BlogPosting";s:8:"headline";s:11:"%seo_title%";s:13:"datePublished";s:20:"%date(Y-m-dTH:i:sP)%";s:12:"dateModified";s:24:"%modified(Y-m-dTH:i:sP)%";s:6:"author";a:2:{s:5:"@type";s:6:"Person";s:4:"name";s:5:"Jared";}s:8:"metadata";a:3:{s:5:"title";s:7:"Article";s:9:"isPrimary";b:1;s:4:"type";s:8:"template";}}'
rank_math_analytic_object_id:
  - 72
categories:
  - Phaser 3
series:
  - Build a Space Shooter with Phaser 3
tags:
  - game dev
  - phaser
  - phaser3

---
In the last part of this course, &#8220;Build a Space Shooter with Phaser 3&#8221;, we have added the bulk of our code for our space shooter. We have covered adding enemies, player lasers, enemy lasers, frustum culling, and collisions in the last part. There are a few things we will finish up in this part to conclude this course. We will be adding a scrolling background, filling in the main menu, and create the game over screen.

We will start by adding the scrolling background. The scrolling background will have multiple, scrolling at different speeds. First, let&#8217;s go to our `Entities.js` file. At bottom of the file, we can add a new class, `ScrollingBackground`. It does not need to extend anything.

{{<highlight js>}}
class ScrollingBackground {
  constructor(scene, key, velocityY) {
    
  }
}
{{</highlight>}}

Our constructor will be taking in the scene we instantiate a scrolling background, and the image key of our star background. We will first set the scene of the instance to our parameter we&#8217;ve taken in. We will also store our keys into an instance of a scrolling background.

{{<highlight js>}}
this.scene = scene;
this.key = key;
this.velocityY = velocityY;
{{</highlight>}}

We will be implementing a function called `createLayers`. Before we do however, we need to create a group inside our constructor.

{{<highlight js>}}
this.layers = this.scene.add.group();
{{</highlight>}}

Inside our new `createLayers` function, let&#8217;s add the following code to create sprites out of the image key we&#8217;re given.

{{<highlight js>}}
for (var i = 0; i < 2; i++) {
      // creating two backgrounds will allow a continuous scroll
      var layer = this.scene.add.sprite(0, 0, this.key);
      layer.y = (layer.displayHeight * i);
      var flipX = Phaser.Math.Between(0, 10) >= 5 ? -1 : 1;
      var flipY = Phaser.Math.Between(0, 10) >= 5 ? -1 : 1;
      layer.setScale(flipX * 2, flipY * 2);
      layer.setDepth(-5 - (i - 1));
      this.scene.physics.world.enableBody(layer, 0);
      layer.body.velocity.y = this.velocityY;

      this.layers.add(layer);
    }
{{</highlight>}}

The above code iterates through each key we take in. For each key, we create two sprites with the key at each iteration of the first `for` loop. We then add the sprite to our `layers` group. We then apply a downwards velocity in which each layer is slower the farther back they are based on the value of `i`.

We can then call `createLayers` at the bottom of our constructor.

{{<highlight js>}}
this.createLayers();
{{</highlight>}}

Now we can head over to `SceneMain.js` and initialize the scrolling background. Insert the following code before we instantiate the player and add it after we define `this.sfx`.

{{<highlight js>}}
this.backgrounds = [];
for (var i = 0; i < 5; i++) { // create five scrolling backgrounds
  var bg = new ScrollingBackground(this, "sprBg0", i * 10);
  this.backgrounds.push(bg);
}
{{</highlight>}}

Try running the game, you should see a the stars behind the player. All four backgrounds should be drawn now. We can now head back to `Entities.js` and add an `update` function with the following code inside:

{{<highlight js>}}
if (this.layers.getChildren()[0].y > 0) {
      for (var i = 0; i < this.layers.getChildren().length; i++) {
        var layer = this.layers.getChildren()[i];
        layer.y = (-layer.displayHeight) + (layer.displayHeight * i);
      }
    }
{{</highlight>}}

The above code allows the background layers to wrap back around to the bottom. If we didn&#8217;t have this code, the backgrounds will just move off-screen and there will remain the black background. We can go back to `SceneMain.js` and call the `update` function of our scrolling background instance. In the `update` function of `SceneMain`, add the following code:

{{<highlight js>}}
for (var i = 0; i < this.backgrounds.length; i++) {
      this.backgrounds[i].update();
    }
{{</highlight>}}

That concludes adding our background to the game! If we run the game we should see multiple background layers scrolling down at different speeds.

We can finish up by adding our main menu and game over screen. 

Navigate to `SceneMainMenu` and remove the line that starts `SceneMain`. Before we continue however, we should a sound effect object for SceneMainMenu. Add the following to the very top of the `create` function:

{{<highlight js>}}
this.sfx = {
  btnOver: this.sound.add("sndBtnOver"),
  btnDown: this.sound.add("sndBtnDown")
};
{{</highlight>}}

We can then add the play button to the `create` function by adding a sprite.

{{<highlight js>}}
this.btnPlay = this.add.sprite(
  this.game.config.width * 0.5,
  this.game.config.height * 0.5,
  "sprBtnPlay"
);
{{</highlight>}}

In order to start `SceneMain`, we will need to first set our sprite as interactive. Add the following directly below where we defined `this.btnPlay`:

{{<highlight js>}}
this.btnPlay.setInteractive();
{{</highlight>}}

Since we set our sprite as being interactive, we can now add pointer events such as over, out, down, and up. We can execute code when each of these events are triggered by the mouse or tap. The first event we will add is the `pointerover` event. We will be changing the texture of the button to our `sprBtnPlayHover.png` image when the pointer moves over the button. Add the following after we set our button as interactive:

{{<highlight js>}}
this.btnPlay.on("pointerover", function() {
  this.btnPlay.setTexture("sprBtnPlayHover"); // set the button texture to sprBtnPlayHover
  this.sfx.btnOver.play(); // play the button over sound
}, this);
{{</highlight>}}

If we run the game and move the mouse over the button we should see:<figure class="wp-block-image">

<img loading="lazy" width="720" height="960" src="https://learn.yorkcs.com/wp-content/uploads/2019/02/screen-main-menu.jpg" alt="" class="wp-image-538" /> </figure> 

Now we can add the `pointerout` event. In this event we will reset the texture back to the normal play button image. Add the following under where we define the `pointerover` event:

{{<highlight js>}}
this.btnPlay.on("pointerout", function() {
  this.setTexture("sprBtnPlay");
});
{{</highlight>}}

If we run the game again and move the mouse over the button, then off, we should see the button texture reset to the default image.

Next, we can add the `pointerdown` event. This is where we will change the texture of the play button to `sprBtnPlayDown.png`.

{{<highlight js>}}
this.btnPlay.on("pointerdown", function() {
  this.btnPlay.setTexture("sprBtnPlayDown");
  this.sfx.btnDown.play();
}, this);
{{</highlight>}}

If we run the game, we should see the button texture change to `sprBtnPlayDown.png` when we move the mouse over the button and click. We can then add the `pointerup` event to reset the button texture after we click.

{{<highlight js>}}
this.btnPlay.on("pointerup", function() {
  this.setTexture("sprBtnPlay");
}, this);
{{</highlight>}}

<div class="wp-block-image">
  <figure class="aligncenter"><img loading="lazy" width="714" height="914" src="https://learn.yorkcs.com/wp-content/uploads/2019/02/p3ss_play_button.gif" alt="" class="wp-image-547" /></figure>
</div>

We can a line one more line inside our `pointerup` event to start `SceneMain`. The final `pointerup` event should look like:

{{<highlight js>}}
this.btnPlay.on("pointerup", function() {
  this.btnPlay.setTexture("sprBtnPlay");
  this.scene.start("SceneMain");
}, this);
{{</highlight>}}

When we run the game and click the play button, it should now start `SceneMain`!

<div class="wp-block-image">
  <figure class="aligncenter"><img loading="lazy" width="714" height="914" src="https://learn.yorkcs.com/wp-content/uploads/2019/02/p3ss_play_button_click.gif" alt="" class="wp-image-552" /><figcaption>It works!</figcaption></figure>
</div>

There are now just a couple things we can do to finish up our main menu. The first is adding a title. To add our title, we can create text. Add the following under the `pointerup` event

{{<highlight js>}}
this.title = this.add.text(this.game.config.width * 0.5, 128, "SPACE SHOOTER", {
  fontFamily: 'monospace',
  fontSize: 48,
  fontStyle: 'bold',
  color: '#ffffff',
  align: 'center'
});
{{</highlight>}}

To center the title, we can set the origin of the text to half the width, and half the height. We can do this by writing the following under our title definition:

{{<highlight js>}}
this.title.setOrigin(0.5);
{{</highlight>}}

The last thing we will do for our main menu is add our scrolling background in. We can copy the code from the create function of `SceneMain` to `SceneMainMenu`, but the code is available below as well.

{{<highlight js>}}
this.backgrounds = [];
for (var i = 0; i < 5; i++) {
  var keys = ["sprBg0", "sprBg1"];
  var key = keys[Phaser.Math.Between(0, keys.length - 1)];
  var bg = new ScrollingBackground(this, key, i * 10);
  this.backgrounds.push(bg);
}
{{</highlight>}}

We can also create the `update` function as well. In the `update` function we will update our background layers. Add the following to the `update` function to update our scrolling backgrounds.

{{<highlight js>}}
for (var i = 0; i < this.backgrounds.length; i++) {
  this.backgrounds[i].update();
}
{{</highlight>}}

Try running the game now. You may notice some green squares in the top-left corner of the screen.<figure class="wp-block-image">

<img loading="lazy" width="714" height="914" src="https://learn.yorkcs.com/wp-content/uploads/2019/02/p3ss_background_missing.gif" alt="" class="wp-image-558" /> </figure> 

The reason why we are not seeing our backgrounds, is because they haven&#8217;t been loaded yet. They have been loaded in `SceneMain`, but if we look at our scene array in `game.js`, `SceneMain` is after `SceneMainMenu` so we are not able to access loaded content from `SceneMain`. To fix this, we will have to move the lines loading `sprBg0.png` and `sprBg1.png` to the `preload` function of `SceneMainMenu`. The `preload` function of `SceneMainMenu` should look similar to:

{{<highlight js>}}
this.load.image("sprBg0", "content/sprBg0.png");
this.load.image("sprBg1", "content/sprBg1.png");
this.load.image("sprBtnPlay", "content/sprBtnPlay.png");
this.load.image("sprBtnPlayHover", "content/sprBtnPlayHover.png");
this.load.image("sprBtnPlayDown", "content/sprBtnPlayDown.png");
this.load.image("sprBtnRestart", "content/sprBtnRestart.png");
this.load.image("sprBtnRestartHover", "content/sprBtnRestartHover.png");
this.load.image("sprBtnRestartDown", "content/sprBtnRestartDown.png");

this.load.audio("sndBtnOver", "content/sndBtnOver.wav");
this.load.audio("sndBtnDown", "content/sndBtnDown.wav");
{{</highlight>}}

When we now run the game, we should see background looking how it should.<figure class="wp-block-image">

<img loading="lazy" width="478" height="638" src="https://learn.yorkcs.com/wp-content/uploads/2019/02/spaceshooter_mainmenu.gif" alt="" class="wp-image-584" /> </figure> 

The final part of this course will be fleshing out `SceneGameOver` and adding the scene start code in the appropriate colliders.

We can copy over the title code from `SceneMainMenu` to `SceneGameOver`. In the `create` function of `SceneGameOver`, we can add the following code to create our title. This title code is essentially identical to the code we used previously. The only change we make is changing the string to draw from `"SPACE SHOOTER"` to `"GAME OVER"`.

{{<highlight js>}}
this.title = this.add.text(this.game.config.width * 0.5, 128, "GAME OVER", {
  fontFamily: 'monospace',
  fontSize: 48,
  fontStyle: 'bold',
  color: '#ffffff',
  align: 'center'
});
this.title.setOrigin(0.5);
{{</highlight>}}

Next we can add our sound effect object, as we did with both `SceneMainMenu` and `SceneMain`.

{{<highlight js>}}
this.sfx = {
  btnOver: this.sound.add("sndBtnOver"),
  btnDown: this.sound.add("sndBtnDown")
};
{{</highlight>}}

Once we have added the game over title and sound effect object, we can add in the restart button. The code is pretty much identical to that which we used with the play button. Add the following to the `create` function of `SceneGameOver`:

{{<highlight js>}}
this.btnRestart = this.add.sprite(
      this.game.config.width * 0.5,
      this.game.config.height * 0.5,
      "sprBtnRestart"
    );

    this.btnRestart.setInteractive();

    this.btnRestart.on("pointerover", function() {
      this.btnRestart.setTexture("sprBtnRestartHover"); // set the button texture to sprBtnPlayHover
      this.sfx.btnOver.play(); // play the button over sound
    }, this);

    this.btnRestart.on("pointerout", function() {
      this.setTexture("sprBtnRestart");
    });

    this.btnRestart.on("pointerdown", function() {
      this.btnRestart.setTexture("sprBtnRestartDown");
      this.sfx.btnDown.play();
    }, this);

    this.btnRestart.on("pointerup", function() {
      this.btnRestart.setTexture("sprBtnRestart");
      this.scene.start("SceneMain");
    }, this);
{{</highlight>}}

After our button code, we can create our background layers. As we have before, we can add the following code to the `create` function:

{{<highlight js>}}
this.backgrounds = [];
for (var i = 0; i < 5; i++) {
  var keys = ["sprBg0", "sprBg1"];
  var key = keys[Phaser.Math.Between(0, keys.length - 1)];
  var bg = new ScrollingBackground(this, key, i * 10);
  this.backgrounds.push(bg);
}
{{</highlight>}}

Then add our update code to update the backgrounds in the `update` function:

{{<highlight js>}}
for (var i = 0; i < this.backgrounds.length; i++) {
  this.backgrounds[i].update();
}
{{</highlight>}}

We finished adding the game over title, restart button, and scrolling background layers. That&#8217;s great, except we can&#8217;t see our changes yet because we haven&#8217;t started `SceneGameOver` anywhere yet. To change this, we can go to our `Entities.js` file and create an `onDestroy` function for our player. The plan is, we will want to create an event that will start `SceneGameOver` after a slight delay. Inside our new `onDestroy` function, we can add the following code:

{{<highlight js>}}
this.scene.time.addEvent({ // go to game over scene
  delay: 1000,
  callback: function() {
    this.scene.scene.start("SceneGameOver");
  },
  callbackScope: this,
  loop: false
});
{{</highlight>}}

In order to finish with our `onDestroy` function, we will need to go back to `SceneMain.js` and look in the `create` function. Specifically we will have to call the player&#8217;s `onDestroy` function in every collider that involves the player. Just after we call `player.explode(false);`, we can insert: `player.onDestroy();`

There we have it! This concludes the end of our five part course, &#8220;Build a Space Shooter with Phaser 3&#8221;!

There are quite a features you could add to this project as well. A few I can think of are:

  * add lives
  * add a score
  * add increasing difficulty
  * add upgrade
  * add bosses

If you decide to expand this project, I would really love to hear about it! Add a comment below or email me at jared.york@jaredyork.com. 🙂

  


We covered the majority of the components you need to make your own games with Phaser 3. I would also like to thank the Phaser 3 team for making such an awesome HTML5 game framework and for all the work they have done. You can learn more about Phaser at their official website, [here][1]. As always, please feel free to ask me questions, and I will be more than glad to help. I&#8217;m thinking about creating more free and paid courses in the future. Let me know what you would like a course about and I may consider it. 🙂

The final code for this course is available on [GitHub][2].

If you would like to receive updates on future courses I release, please feel free to fill out the [form][3].

 [1]: https://phaser.io/
 [2]: https://github.com/jaredyork/CoursePhaser3SpaceShooter
 [3]: https://docs.google.com/forms/d/e/1FAIpQLSfSAg6xMDrk44pbmIlVUqLwjm9FHaKPdy_WcbHUmLWWyXMQag/viewform