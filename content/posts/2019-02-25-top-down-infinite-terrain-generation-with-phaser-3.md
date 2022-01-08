---
title: Top-down Infinite Terrain Generation with Phaser 3
author: Jared
type: post
date: 2019-02-26T00:45:30+00:00
url: /2019/02/25/top-down-infinite-terrain-generation-with-phaser-3/
featured_image: /wp-content/uploads/2019/02/infiniteterrainsocialshorter.gif
rank_math_internal_links_processed:
  - 1
rank_math_seo_score:
  - 78
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
rank_math_schema_Article:
  - 'a:6:{s:5:"@type";s:11:"BlogPosting";s:8:"headline";s:11:"%seo_title%";s:13:"datePublished";s:20:"%date(Y-m-dTH:i:sP)%";s:12:"dateModified";s:24:"%modified(Y-m-dTH:i:sP)%";s:6:"author";a:2:{s:5:"@type";s:6:"Person";s:4:"name";s:5:"Jared";}s:8:"metadata";a:3:{s:5:"title";s:7:"Article";s:9:"isPrimary";b:1;s:4:"type";s:8:"template";}}'
rank_math_analytic_object_id:
  - 68
categories:
  - Phaser 3

---
In this tutorial, we will be creating an infinitely, procedurally generated, map with Phaser 3. &nbsp;You can visit Phaser’s official [website][1] to find out more information about Phaser.  


#### Tutorial Requirements

  * Basic to intermediate knowledge of JavaScript
  * Web server
  * Tutorial assets
  * Code editor (not required, but highly recommended)

## Ensure a Web Server is Set Up  


Although Phaser games are ran in the browser, unfortunately you can’t just run a local HTML file directly from your file system. &nbsp;When requesting files over http, the security of the server only allows you to access files you’re allowed to. When loading a file from the local file system (the file:// protocol), your browser highly restricts it for obvious security reasons. &nbsp;It’s no good to allow code on a website to read anything in your raw file system. Because of this, we will need to host our game on a local web server.  


We recommend checking out Phaser’s official guide, “[Getting Started with Phaser 3][2]”, to learn which web server is compatible with your system and there are links to each one. &nbsp;The guide also provides some detailed summaries on each of the various web servers mentioned.

## Create the Folders and Files Needed  


First, find the directory where your web server hosts files from (WAMP Server, for example, hosts files from the www directory within it’s installation folder at C:/wamp64.) &nbsp;Once you have found the location, create a new folder inside it and call it anything you want.  


Next, enter the folder and create a new file called, “index.html”. &nbsp;Our index file is where we will declare the location of our Phaser script and the rest of our game scripts.  


We also need to create two folders, I called the first one content for our project’s content (just sprites for this tutorial), and another one, js, which will contain the scripts for our game. &nbsp;Feel free to name these two folders anything you wish. One of the folders just needs to contain the content for our project, and the other for JavaScript files. Since we have our folder for content and JavaScript, create three new files inside the newly created folder for JavaScript: Entities.js, SceneMain.js and game.js. &nbsp;I will explain what those files do shortly, but first we need to add the content to our content folder.  


So far, the file structure should look like:  


<pre class="wp-block-preformatted">(game folder)/<br />|_index.html<br />|_js/<br />  |_Entities.js<br />  |_game.js<br />  |_SceneMain.js<br /><br /></pre>

To add content to this project, we first need content. &nbsp;I have pre-made some assets for this course, which can be downloaded [here][3].  


#### Content needed:  


Sprites (images)

  * sprGrass.png
  * sprSand.png
  * sprWater.png (animation, multiple frames in a horizontal strip)

Once you have downloaded the assets (or made your own), we will move those files into the content directory we made.  


One of the last steps we need to do before jumping in, is downloading the latest Phaser script. &nbsp;A common method of acquiring this (there are multiple), is to head over to GitHub (specifically [here][4]) and download the script meant for distribution. &nbsp;You can pick either phaser.js or phaser.min.js. The phaser.js file contains the source code for Phaser in a readable form, which is useful for contributing to Phaser, or just to understand how something works under-the-hood. &nbsp;The other file, phaser.min.js is meant for distribution, and is compressed to reduced file size. For our purposes, it won’t really matter which one we download, though I will use phaser.js. Click the the link of either script, and you will be greeted by a page that displays a “View raw” button, near the center of the page, about halfway down. &nbsp;Next, click the “View raw” link, then right click anywhere on the page of code that appears. There should be dropdown menu that appears after right clicking where you can then click “Save Page As” or something similar. A save dialog should appear where you can save the Phaser file to the JavaScript directory we created earlier.  


Now it’s time for the last step before we start programming. &nbsp;For this tutorial we will be using what is called, Perlin noise. &nbsp;Don’t worry about what that means right now. The only thing we need at this point is a JavaScript library that can provide some functions to generate 2D Perlin noise. &nbsp;The library we will specifically use can be found on GitHub [here][5]. &nbsp;Visit the link, and click the green “Clone or download” button, then click the “Download ZIP”. &nbsp;Extract the folder, then copy the “noisejs-master” folder into the JavaScript folder we created.  


Now we can finally jump right in to the code! &nbsp;The first file we will add to is index.html. Let’s define the markup for our HTML file, where we will define our scripts.  

{{<highlight html>}}
<!DOCTYPE html>
<html>
    <head>
        <meta charset=”utf-8”>
        <meta lang=”en-us”>
        <title>Infinite Terrain</title>
    </head>

    <body>
        <script src=”js/phaser.js”></script>
        <script src=”js/noisejs-master/perlin.js”></script>
        <script src=”js/Entities.js”></script>
        <script src=”js/SceneMain.js”></script>
        <script src=”js/game.js”></script>
    </body>
</html>
{{</highlight>}}

Next, we can head over to game.js, and define the configuration we want Phaser to create a game with. &nbsp;In the game.js file, let’s add the following:  

{{<highlight js>}}
var config = {
    type: Phaser.WEBGL,
    width: 640,
    height: 640,
    backgroundColor: “black”,
    physics: {
        default: “arcade”,
        arcade: {
            Gravity: { x: 0, y: 0 }
        }
    },
    scene: [
        SceneMain
    ],
    pixelArt: true,
    roundPixels: true
};

var game = new Phaser.Game(config);
{{</highlight>}}

Next, let’s go to the Entities.js file. &nbsp;When we generate infinite terrain, we will not be storing an array of all the tiles in the map. &nbsp;Storing each tile individually would not be scalable, it would crash the browser after moving over enough terrain, and it would be impossible to store it in the browser. &nbsp;Instead, we will be using a chunk system. If you’ve ever played Minecraft, you will probably know that chunks of blocks are loaded around the player. When the player moves out of the range of a loaded chunk, the chunk is the unloaded. &nbsp;We will be building a very similar system in this tutorial. To start, we can create an object that represents a chunk. To do this, we will be using the ES6 class syntax, which is essentially syntactic sugar of a normal JavaScript object. &nbsp;Classes are useful for organizing the structure of an object, and provides an easy way of adding functions.  


Let’s start by adding the chunk class and also give it a constructor. The constructor should take in three parameters: scene, x, and y:  

{{<highlight js>}}
class Chunk {
    constructor(scene, x, y) {
        
    }
}
{{</highlight>}}

By default, scene, x, and y will not be stored in an instance of this class. &nbsp;To store it, we can simply assign the parameters to the instance of the class by using the this keyword. &nbsp;The this keyword means the current instance that’s having it’s code interpreted. Inside the constructor, add the following:  

{{<highlight js>}}
this.scene = scene;
this.x = x;
this.y = y;
{{</highlight>}}

Each chunk will contain a Phaser group, which will store all of the tiles for that specific chunk. &nbsp;We will also want to add a boolean property which will determine whether the chunk is loaded or not. &nbsp;Let’s add a couple more lines to our constructor:  

{{<highlight js>}}
this.tiles = this.scene.add.group();
this.isLoaded = false;
{{</highlight>}}

There are two more functions we want to define in our Chunk class: unload, and load. &nbsp;We will start with unload. After the constructor, but still within the Chunk class, add the following:

{{<highlight js>}}
unload() {
    if (this.isLoaded) {
        this.tiles.clear(true, true);

        this.isLoaded = false;
    }
}
{{</highlight>}}

When unload is called, the chunk will check if it is loaded, if so, remove all the tiles from the group and set the state of isLoaded to false for that chunk.  


The next function we need to create is load. &nbsp;This function will create the tiles for the chunk, if the chunk is not loaded already. &nbsp;When creating the tiles, we will also be generating the Perlin noise value for the X and Y position of that specific tile. &nbsp;We can then check if the value is between various ranges and we generate different terrain tiles accordingly. First we’ll start by creating the load function, and creating the condition which checks if the chunk is not loaded:  

{{<highlight js>}}
load() {
    if (!this.isLoaded) {
        
    }
}
{{</highlight>}}

Next we will want to iterate through each X and Y tile position in the chunk. &nbsp;We will set a property in SceneMain which will determine the chunk size and tile size but for now, add the following inside the if statement:  

{{<highlight js>}}
for (var x = 0; x < this.scene.chunkSize; x++) {
    for (var y = 0; y < this.scene.chunkSize; y++) {
        
    }
}
{{</highlight>}}

Basically, once each tile in the current column is created, then it moves on to the next column and create all the tiles in that column, etc. &nbsp;Here’s a very crude diagram to help visualize this:  

![](https://learn.yorkcs.com/wp-content/uploads/2019/02/3CF9CDEA-C1EB-4101-B234-CE954089A142.jpeg)

The next step to create our tiles, is to define two variables which will hold the X position, and Y position of the tile, respectively. &nbsp;Add the following inside the second for loop:  

{{<highlight js>}}
var tileX = (this.x * (this.scene.chunkSize * this.scene.tileSize)) + (x * this.scene.tileSize);
var tileY = (this.y * (this.scene.chunkSize * this.scene.tileSize)) + (y * this.scene.tileSize);
{{</highlight>}}

Now is the (most?) fun part. &nbsp;It’s time to generate our perlin noise value. &nbsp;Add the following code after the above two variables we declared:  

{{<highlight js>}}
var perlinValue = noise.perlin2(tileX / 100, tileY / 100);
{{</highlight>}}

Feel free to change the value we divide by, in this case I used 100, but you can try 50, or 1000, or anything. &nbsp;Pretty much all that value does is determine how zoomed-in the Perlin noise is.  


Underneath that, add a local variable for determining the image key, as well as one for setting the optional animation key:  

{{<highlight js>}}
var key = “”;
var animationKey = “”;
{{</highlight>}}

Now that we’ve generate a perlin noise value, we can check decimal ranges to determine what tile we want to create. &nbsp;Add this next code block under our previous line:  

{{<highlight js>}}
if (perlinValue < 0.2) {
    key = “sprWater”;
    animationKey = “sprWater”;
}
else if (perlinValue >= 0.2 && perlinValue < 0.3) {
    key = “sprSand”;
}
else if (perlinValue >= 0.3) {
    key = “sprGrass”;
}
{{</highlight>}}

Now we can finally create the instance of the tile and add it to the tiles group. &nbsp;If an animation key is set, also play the animation specified by the animation key. &nbsp;Add the following under the last bit of code:  

{{<highlight js>}}
var tile = new Tile(this.scene, tileX, tileY, key);

if (animationKey !== “”) {
    tile.play(animationKey);
}

this.tiles.add(tile);
{{</highlight>}}

To finish up, let’s set our chunk to be loaded just after both for loops, but still within the not loaded condition:  

{{<highlight js>}}
this.isLoaded = true;
{{</highlight>}}

When loading is completed for a chunk, we want to set it’s isLoaded value to true.  


We can now move on to the Tile class. &nbsp;The Tile class will just extend a Phaser sprite for now, but it could be handy for adding interaction, or special properties to your tiles in the future. &nbsp;Let’s add our tile class:

{{<highlight js>}}
class Tile extends Phaser.GameObjects.Sprite {
    constructor(scene, x, y, key) {
        super(scene, x, y, key);
        this.scene = scene;
        this.scene.add.existing(this);
        this.setOrigin(0);
    }
}
{{</highlight>}}

Inside the constructor, we ensure that a tile instance will be added to the display list of the current Scene. &nbsp;We also set the origin to the top left corner. The cool thing about the setOrigin method is we only have to type the first parameter if we want a value to apply to both the X and Y axis &nbsp;Great! We are now finished with the Entities.js file.  


Let’s hop on over to SceneMain.js. &nbsp;The first thing we want to do in this file is declare our class, SceneMain, which should extend Phaser.Scene:  

{{<highlight js>}}
class SceneMain extends Phaser.Scene {

}
{{</highlight>}}

The next thing we want to do is add our constructor as well as four functions we will be using:  

{{<highlight js>}}
constructor() {
    super({ key: “SceneMain” });
}

preload() {

}

create() {

}

getChunk(x, y) {

}

update() {

}
{{</highlight>}}

Starting with the preload function, let’s add the loading code for our three image files:  

{{<highlight js>}}
this.load.spritesheet(“sprWater”, “content/sprWater.png”, {
    frameWidth: 16,
    frameHeight: 16
});
this.load.image(“sprSand”, “content/sprSand.png”);
this.load.image(“sprGrass”, “content/sprGrass.png”);
{{</highlight>}}

We are now finished loading our project’s content! &nbsp;The next step is to fill in the create function. Inside the create function, add the following:  

{{<highlight js>}}
this.anims.create({
    key: “sprWater”,
    frames: this.anims.generateFrameNumbers(“sprWater”),
    frameRate: 5,
    repeat: -1
});

this.chunkSize = 16;
this.tileSize = 16;
this.cameraSpeed = 10;

this.cameras.main.setZoom(2);

this.followPoint = new Phaser.Math.Vector2(
    this.cameras.main.worldView.x + (this.cameras.main.worldView.width * 0.5),
    this.cameras.main.worldView.y + (this.cameras.main.worldView.height * 0.5)
);

this.chunks = [];

this.keyW = this.input.keyboard.addKey(Phaser.Input.Keyboard.KeyCodes.W);
this.keyS = this.input.keyboard.addKey(Phaser.Input.Keyboard.KeyCodes.S);
this.keyA = this.input.keyboard.addKey(Phaser.Input.Keyboard.KeyCodes.A);
this.keyD = this.input.keyboard.addKey(Phaser.Input.Keyboard.KeyCodes.D);
{{</highlight>}}

The first thing we do in the code above is create the animation for our water tile. &nbsp;We are also creating three properties. The property, chunkSize, defines the size of a chunk by the amount of tiles for both the width and height of the chunk. &nbsp;Since chunkSize is currently set to 16, the chunk would be 16 tiles in width, and 16 tiles in height. The next thing we do in the create function is set the zoom level of the camera. &nbsp;I have set the zoom to 2X the default. I also created a two-dimensional vector (it’s a useful object for defining X and Y positions in graphical programming). This 2D vector contains the X and Y values for what I call the “follow point”. &nbsp;The follow point will be used as the point in which the camera will be centered on. In a normal game, you could center the camera on the player sprite instead. However, since in this project we’re strictly covering just the mechanics of an infinite procedural terrain generator, I will leave adding the player as an exercise for the reader. 🙂 &nbsp;We are also adding four properties which will soon be used for checking if the corresponding key is down. The four properties are for the W key, S key, A key, and D key.  


We can now take a look at the getChunk function. &nbsp;The getChunk function will be extremely useful for getting the chunk at a certain chunk position. &nbsp;Inside the getChunk function, add the following to retrieve the chunk at a specific X, Y, position:  

{{<highlight js>}}
var chunk = null;
for (var i = 0; i < this.chunks.length; i++) {
    if (this.chunks[i].x == x && this.chunks[i].y == y) {
        chunk = this.chunks[i];
    }
}
return chunk;
{{</highlight>}}

Great! &nbsp;Now we can now fill in the update function. &nbsp;Before proceeding, the update function will contain quite a bit of code. &nbsp;The sequence of instructions the update function will execute each frame is the following:

  * Get the chunk position that the follow point is in.
  * Create chunks around the follow point if they don’t exist.
  * Load chunks around the follow point if they do exist. &nbsp;Also if a chunk exists, but is outside a certain radius of chunks, unload the chunk.
  * Move the camera in the corresponding direction based on the key that’s down.
  * Center the camera on the follow point.

We’ll first start with getting the chunk position the follow point is in. &nbsp;Knowing the chunk position that the follow point is in is critical because our chunk creation and chunk loading all happens relative to the chunk the follow point is in. &nbsp;We will essentially be snapping the position of the follow point to a grid, with each cell being the size of the chunk as a world position. We then divide that number down by the chunk size and tile size so we get our proper chunk position. &nbsp;Add the following code to the update function:  

{{<highlight js>}}
var snappedChunkX = (this.chunkSize * this.tileSize) * Math.round(this.followPoint.x / (this.chunkSize * this.tileSize));
var snappedChunkY = (this.chunkSize * this.tileSize) * Math.round(this.followPoint.y / (this.chunkSize * this.tileSize));

snappedChunkX = snappedChunkX / this.chunkSize / this.tileSize;
snappedChunkY = snappedChunkY / this.chunkSize / this.tileSize;
{{</highlight>}}

This code retrieves the chunk position that the follow point is in. &nbsp;The next portion of code will create chunks around this chunk position if they do not exist yet. &nbsp;Add the following block of code:  

{{<highlight js>}}
for (var x = snappedChunkX - 2; x < snappedChunkX + 2; x++) {
    for (var y = snappedChunkY - 2; y < snappedChunkY + 2; y++) {
        var existingChunk = this.getChunk(x, y);

        if (existingChunk == null) {
            var newChunk = new Chunk(this, x, y);
            this.chunks.push(newChunk);
        }
    }
}
{{</highlight>}}

The above code creates chunks in a radius of two chunks around the follow point. &nbsp;The next step is to add in the chunk loading and unloading logic. Add the following block under the previous:  

{{<highlight js>}}
for (var i = 0; i < this.chunks.length; i++) {
    var chunk = this.chunks[i];

    if (Phaser.Math.Distance.Between(
        snappedChunkX,
        snappedChunkY,
        chunk.x,
        chunk.y
    ) < 3) {
        if (chunk !== null) {
            chunk.load();
        }
    }
    else {
        if (chunk !== null) {
            chunk.unload();
        }
    }
}
{{</highlight>}}

The last part to this infinite terrain generation tutorial is adding in the camera movement and centering the camera on the follow point. &nbsp;Let’s add the following code to add camera movement.  

{{<highlight js>}}
if (this.keyW.isDown) {
    this.followPoint.y -= this.cameraSpeed;
}
if (this.keyS.isDown) {
    this.followPoint.y += this.cameraSpeed;
}
if (this.keyA.isDown) {
    this.followPoint.x -= this.cameraSpeed;
}
if (this.keyD.isDown) {
    this.followPoint.x += this.cameraSpeed;
}
{{</highlight>}}

To center the camera, it’s an easy one-liner:  

{{<highlight js>}}
this.cameras.main.centerOn(this.followPoint.x, this.followPoint.y);
{{</highlight>}}

There we have it! &nbsp;If we navigate to our page in the browser, we should something like the this:

![](https://learn.yorkcs.com/wp-content/uploads/2019/02/infiniteterrain.gif "It works!")

This concludes this tutorial on infinite procedural terrain generation! &nbsp;The final code for this tutorial can be found on [GitHub][6]. I’m looking forward to hearing your comments, suggestions, and feedback on this tutorial. &nbsp;Feel free to email me at <jared.york@yorkcs.com>. I would love to hear what you can do with this. &nbsp;I could see this code easily be adapted for an RPG game, or a game similar to Minicraft, etc. &nbsp;If you build something cool with this, tweet it at me! My Twitter handle is [@jaredyork_][7]. &nbsp;If you would like to hear about more of our tutorials and courses, be sure to fill out the [form][8].

 [1]: http://phaser.io/
 [2]: https://phaser.io/tutorials/getting-started-phaser3/part2
 [3]: http://www.mediafire.com/file/9o4zkiq93uukske/InfiniteTerrainContent.zip/file
 [4]: https://github.com/photonstorm/phaser/tree/master/dist
 [5]: https://github.com/josephg/noisejs
 [6]: https://github.com/jaredyork/TutorialInfiniteTerrain
 [7]: https://twitter.com/jaredyork_
 [8]: https://docs.google.com/forms/d/e/1FAIpQLSfSAg6xMDrk44pbmIlVUqLwjm9FHaKPdy_WcbHUmLWWyXMQag/viewform