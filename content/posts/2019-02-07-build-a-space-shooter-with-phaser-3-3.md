---
title: Build a Space Shooter with Phaser 3 – 3
author: Jared
type: post
date: 2019-02-07T13:03:36+00:00
url: /2019/02/07/build-a-space-shooter-with-phaser-3-3/
featured_image: /wp-content/uploads/2019/02/thumbnail_wp_part3.jpg
rank_math_seo_score:
  - 75
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
rank_math_focus_keyword:
  - phaser
rank_math_robots:
  - 'a:1:{i:0;s:5:"index";}'
rank_math_schema_Article:
  - 'a:6:{s:5:"@type";s:11:"BlogPosting";s:8:"headline";s:11:"%seo_title%";s:13:"datePublished";s:20:"%date(Y-m-dTH:i:sP)%";s:12:"dateModified";s:24:"%modified(Y-m-dTH:i:sP)%";s:6:"author";a:2:{s:5:"@type";s:6:"Person";s:4:"name";s:5:"Jared";}s:8:"metadata";a:3:{s:5:"title";s:7:"Article";s:9:"isPrimary";b:1;s:4:"type";s:8:"template";}}'
rank_math_analytic_object_id:
  - 74
categories:
  - Phaser 3
series:
  - Build a Space Shooter with Phaser 3
tags:
  - game dev
  - phaser
  - phaser3

---
In the last part, we finished setting up the basis for our scene files: `SceneMainMenu.js`, `SceneMain.js`, and `SceneGameOver.js`. At this point you can try running the game by navigating to `localhost/(game folder name)/index.html`. There might be a port that&#8217;s needed when viewing files on some web servers, for example, `localhost:8000`. If everything is right, you should see a black rectangle on the page. The black rectangle is the area where your game will be drawn.

It&#8217;s time to dive back into the code. Take a second and open up `SceneMain.js`. When we left off, our `SceneMain.js` should look like:

{{<highlight js>}}
class SceneMain extends Phaser.Scene {
  constructor() {
    super({ key: "SceneMain" });
  }
  create() {
    
  }
}
{{</highlight>}}

At this point we need to add a new function called `preload`. This function should be inserted between `constructor` and `create`. All three functions inside `SceneMain` should look like:

{{<highlight js>}}
constructor() {
    super({ key: "SceneMain" });
  }
  preload() {

  }
  create() {
    
  }
{{</highlight>}}

Inside our new `preload` function, we need to add the code to load our game assets. To load image files, the line you would type inside the `preload` function would be:

{{<highlight js>}}
this.load.image(imageKey, path);
{{</highlight>}}

If we start with our first image file we want to load, `sprBg0.png`, we should add:

{{<highlight js>}}
this.load.image("sprBg0", "content/sprBg0.png");
{{</highlight>}}

The first parameter of `this.load.image` refers to the key (a string) that we will reference the image when we add images and sprites within the game. The second parameter is the path to the image we wish to load.

Lets finish adding the rest of our loading code for our images:

{{<highlight js>}}
this.load.image("sprBg0", "content/sprBg0.png");
this.load.image("sprBg1", "content/sprBg1.png");
this.load.spritesheet("sprExplosion", "content/sprExplosion.png", {
  frameWidth: 32,
  frameHeight: 32
});
this.load.spritesheet("sprEnemy0", "content/sprEnemy0.png", {
  frameWidth: 16,
  frameHeight: 16
});
this.load.image("sprEnemy1", "content/sprEnemy1.png");
this.load.spritesheet("sprEnemy2", "content/sprEnemy2.png", {
  frameWidth: 16,
  frameHeight: 16
});
this.load.image("sprLaserEnemy0", "content/sprLaserEnemy0.png");
this.load.image("sprLaserPlayer", "content/sprLaserPlayer.png");
this.load.spritesheet("sprPlayer", "content/sprPlayer.png", {
  frameWidth: 16,
  frameHeight: 16
});
{{</highlight>}}

The lines that include `spritesheet` means we are loading an animation instead of a static image. A sprite sheet is an image with multiple frames, side-by-side. The third argument of the `load.spritesheet` function is an object defining the frame width and height in pixels. Now we will need to add the loading code for our sounds, which follow the same format as loading images:

{{<highlight js>}}
this.load.audio("sndExplode0", "content/sndExplode0.wav");
this.load.audio("sndExplode1", "content/sndExplode1.wav");
this.load.audio("sndLaser", "content/sndLaser.wav");</pre>
{{</highlight>}}

Once we have loaded our content, we need to add a little bit more code to create our animations. At the top of the `create` function of our screen we will create our animations:

{{<highlight js>}}
this.anims.create({
      key: "sprEnemy0",
      frames: this.anims.generateFrameNumbers("sprEnemy0"),
      frameRate: 20,
      repeat: -1
    });

    this.anims.create({
      key: "sprEnemy2",
      frames: this.anims.generateFrameNumbers("sprEnemy2"),
      frameRate: 20,
      repeat: -1
    });

    this.anims.create({
      key: "sprExplosion",
      frames: this.anims.generateFrameNumbers("sprExplosion"),
      frameRate: 20,
      repeat: 0
    });

    this.anims.create({
      key: "sprPlayer",
      frames: this.anims.generateFrameNumbers("sprPlayer"),
      frameRate: 20,
      repeat: -1
    });
{{</highlight>}}

We also need to add our sounds to some sort of variable or object so we can reference it later. I like to organize my sound references by storing them as values of a sound effect object. If there are more than one sound of a type (say, three explosion sounds), I add an array as the value of a property (going with the last example, I would go with &#8220;explosion&#8221; as the property key.) Let&#8217;s add our sound effect object and hopefully it will make more sense:

{{<highlight js>}}
this.sfx = {
  explosions: [
    this.sound.add("sndExplode0"),
    this.sound.add("sndExplode1")
  ],
  laser: this.sound.add("sndLaser")
};
{{</highlight>}}

We will later be able to play sound effects from our object with, for example:

{{<highlight js>}}
this.sfx.laser.play();
{{</highlight>}}

We will also have to load some images and sounds for the main menu and game over screen. Open up `SceneMainMenu.js` and create a preload function inside `SceneMainMenu`. Inside the new `preload` function add the following to add our buttons and sounds:

{{<highlight js>}}
this.load.image("sprBtnPlay", "content/sprBtnPlay.png");
this.load.image("sprBtnPlayHover", "content/sprBtnPlayHover.png");
this.load.image("sprBtnPlayDown", "content/sprBtnPlayDown.png");
this.load.image("sprBtnRestart", "content/sprBtnRestart.png");
this.load.image("sprBtnRestartHover", "content/sprBtnRestartHover.png");
this.load.image("sprBtnRestartDown", "content/sprBtnRestartDown.png");

this.load.audio("sndBtnOver", "content/sndBtnOver.wav");
this.load.audio("sndBtnDown", "content/sndBtnDown.wav");
{{</highlight>}}

Once we have added the loading code for our images and sounds. We have also created our animations and added our sounds to an object for organization. Now we can navigate back to the game in your browser and a black rectangle should still being showing. If you haven&#8217;t already, open the development tools in the browser you&#8217;re using. If you are using Chrome or Firefox, you can simply press F12 to open it. Look under the Console tab to ensure there are no errors (they are displayed in red.) If you see no errors, we can proceed to proceed with adding the player!

Before we add the player spaceship to our game, we should add a new file in our JavaScript folder called `Entities.js`. This entities script will contain all of the classes for the various entities in our game. We will classify the player, enemies, lasers, etc. as entities. Be sure to also add a reference to `Entities.js` to our `index.html` a line before `SceneMainMenu.js`. After adding the reference to our `Entities.js` file, open it and declare a new class named `Entity`.

{{<highlight js>}}
class Entity {
  constructor() {
    
  }
}
{{</highlight>}}

After declaring our `Entity` class, we need to add some parameters that our Entity class should take in. We will add these parameters between the parenthesis in our `constructor`:

{{<highlight js>}}
constructor(scene, x, y, key, type) {

}
{{</highlight>}}

Each of the parameters we&#8217;ve added to the constructor will be important, because we will be extending `Phaser.GameObjects.Sprite` for all entities we create. Much like how we extended `Phaser.Scene` when we first started this game, we will want to build on top of Phaser&#8217;s `Sprite` class. Because of this, we will have to change `class Entity {` to:

{{<highlight js>}}
class Entity extends Phaser.GameObjects.Sprite {
{{</highlight>}}

As always with extending a class, we will need to add `super` to our `constructor`. Since the player, enemies, and various projectiles we add will have the same basics properties, it helps to keep us from adding redundant, duplicate code. In this way we will be inheriting the properties and functions of the base `Phaser.GameObjects.Sprite` class for all of our entities. Here&#8217;s (a crude diagram) of the inheritance hierarchy we will be implementing:

{{<highlight js>}}
Phaser.GameObjects.Sprite
                   |
                 Entity
                  _|_
               _/  |  \_
            _/     |     \_
          /        |        \
      Player     Enemy     Laser
                   |
                 _/ \_
               /       \
         ChasingShip  GunShip
{{</highlight>}}

All of our entities will have the same basic properties (our scene, x position, y position, image key, and a type string we will use to fetch certain entities if we need to.) Lets add `super` into our constructor which should look like:

{{<highlight js>}}
super(scene, x, y, key);</pre>
{{</highlight>}}

Essentially, what we are doing is taking the parameters in when an `Entity` is instantiated and providing `scene`, `x`, `y`, and `key` to the `Phaser.GameObjects.Sprite` base class.

After adding the `super` keyword to the constructor, on the next line, add the following lines:

{{<highlight js>}}
this.scene = scene;
this.scene.add.existing(this);
this.scene.physics.world.enableBody(this, 0);
this.setData("type", type);
this.setData("isDead", false);
{{</highlight>}}

This piece of code assigns the scene of the `Entity`, as well as adding an instantiated `Entity` to the rendering queue of the scene. We also enable instantiated `Entity`&#8216;s as physics objects in the physics world of the scene. Finally, we define the speed of the player. With that we should be finished adding to our `Entity` class. Now we can move on to creating our `Player` class.

By now, you should know the drill for adding a class. Add one right after the `Entity` class and name it `Player` and ensure it extends `Entity`. Add a constructor to the `Player` class with parameters: `scene`, `x`, `y`, and `key`. Then add our `super` keyword in the constructor providing it the following parameters:

{{<highlight js>}}
super(scene, x, y, key, "Player");
{{</highlight>}}

We also will want a way to determine the speed that the player should move. By adding a `speed` key/value pair for the speed of the player, we can refer to that later for our movement functions. Under the `super` keyword, add the following:

{{<highlight js>}}
this.setData("speed", 200);
{{</highlight>}}

We also will want to add a little piece of code to play the player animation:

{{<highlight js>}}
this.play("sprPlayer");
{{</highlight>}}

To add the movement functions, add the following four functions after the constructor.

{{<highlight js>}}
moveUp() {

}

moveDown() {

}

moveLeft() {

}

moveRight() {

}
{{</highlight>}}

Now add the following lines in each of the functions:

{{<highlight js>}}
moveUp() {
  this.body.velocity.y = -this.getData("speed");
}

moveDown() {
  this.body.velocity.y = this.getData("speed");
}

moveLeft() {
  this.body.velocity.x = -this.getData("speed");
}

moveRight() {
  this.body.velocity.x = this.getData("speed");
}
{{</highlight>}}

These are the movement functions that will be called in the `update` function. Next, add the `update` function directly below the `moveRight` function. Inside the `update` function add: 

{{<highlight js>}}
this.body.setVelocity(0, 0);

this.x = Phaser.Math.Clamp(this.x, 0, this.scene.game.config.width);
this.y = Phaser.Math.Clamp(this.y, 0, this.scene.game.config.height);
{{</highlight>}}

We are now finished with the `Player` class! In the last bit of code, every game update the player&#8217;s velocity will be set to zero. If none of the movement keys are pressed, the player will stay still. The next two lines of the player update code ensures that the player cannot move off-screen. At this point, we can create an instance of the player in the create function of SceneMain. Add the following to the create function of SceneMain:

{{<highlight js>}}
this.player = new Player(
  this,
  this.game.config.width * 0.5,
  this.game.config.height * 0.5,
  "sprPlayer"
);
{{</highlight>}}

This is where we create the instance of the `Player` is created. We can refer to the player anywhere in `SceneMain`. The player is then positioned in the center of the canvas. If you were to try running the game, you still won&#8217;t see the player move yet. This is because we first have to add the `update` function to `SceneMain` and add the movement checks. Since `this.player` is now added, we can now add the `update` function. Add the `update` function right under the `create` function of `SceneMain` and add the following inside:

{{<highlight js>}}
this.player.update();

if (this.keyW.isDown) {
  this.player.moveUp();
}
else if (this.keyS.isDown) {
  this.player.moveDown();
}

if (this.keyA.isDown) {
  this.player.moveLeft();
}
else if (this.keyD.isDown) {
  this.player.moveRight();
}
{{</highlight>}}

Like I mentioned before, `this.player.update();` will run the update code that will keep the player still, as well as ensure it can&#8217;t move off-screen. With the next bit that contains `keyW`, `keyS`, `keyA`, `keyD`, you may wonder why none of those variables have been initialized yet. We will initialize the key variables in a second. These `if` statements check if the corresponding key is down, if so, move the player in the appropriate direction. In the `create` function of `SceneMain`, add the following to initialize our key variables after we initialize the player:

{{<highlight js>}}
this.keyW = this.input.keyboard.addKey(Phaser.Input.Keyboard.KeyCodes.W);
this.keyS = this.input.keyboard.addKey(Phaser.Input.Keyboard.KeyCodes.S);
this.keyA = this.input.keyboard.addKey(Phaser.Input.Keyboard.KeyCodes.A);
this.keyD = this.input.keyboard.addKey(Phaser.Input.Keyboard.KeyCodes.D);
this.keySpace = this.input.keyboard.addKey(Phaser.Input.Keyboard.KeyCodes.SPACE);
{{</highlight>}}

If we run our code now, the player should be able to move via the W, S, A, D keys. In the next part, we will add the ability for the player to shoot lasers (which will use the space key.)

  


And that concludes the third part of &#8220;Build a Space Shooter in Phaser 3&#8221;. If you would like to receive updates on new courses I release via email, feel free to fill out the [form][1].

 [1]: https://docs.google.com/forms/d/e/1FAIpQLSfSAg6xMDrk44pbmIlVUqLwjm9FHaKPdy_WcbHUmLWWyXMQag/viewform