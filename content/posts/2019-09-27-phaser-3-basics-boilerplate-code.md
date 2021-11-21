---
title: 'Phaser 3 Basics: Boilerplate Code'
author: Jared
type: post
date: 2019-09-27T15:21:57+00:00
url: /2019/09/27/phaser-3-basics-boilerplate-code/
featured_image: /wp-content/uploads/2019/09/boilerplate-code-wp.png
rank_math_primary_category:
  - 297
rank_math_focus_keyword:
  - Phaser
rank_math_robots:
  - 'a:1:{i:0;s:5:"index";}'
rank_math_internal_links_processed:
  - 1
rank_math_analytic_object_id:
  - 26
categories:
  - Phaser 3
series:
  - Phaser 3 Basics
tags:
  - beginner
  - tutorial

---
In this part we will be adding the boilerplate code for our Phaser game. There are a few steps we need to do: add code to our index.html file, add some code to an index.html file, defining a game configuration, creating a boot scene, adding a main scene, and creating an instance of our game. If you don&#8217;t have an index.html file yet, or you need to add a script for our game, please check out [part one][1] of this series.

## Index File

In order to be able to play our game, we will need to add some basic code to our index.html file, if you haven&#8217;t already. Add the following code to index.html:

{{<highlight html>}}
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <meta lang="en-us">
        <title>Phaser 3 Tinkering</title>
    </head>
    <body>
        <script src="phaser.js"></script>
        <script src="game.js"></script>
    </body>
</html>
{{</highlight>}}

## Boot Scene

Phaser uses what are known as &#8220;Scenes,&#8221; to define different states within a game. For example, the main menu, the game world, and the game over screen would all be known as a scene in the Phaser framework. Once you load assets in a scene, all scenes listed after it will be able to access the assets you&#8217;ve loaded. We can take advantage of this mechanic by creating a boot scene. We can load our images and sounds in the scene for use by a main menu, play state, etc.

{{<highlight js>}}
class SceneBoot extends Phaser.Scene {
    constructor() {
        super({ key: "SceneBoot" });
    }

    preload() {

    }

    create() {
       this.scene.start("SceneMain");
    }
}
{{</highlight>}}

## Main Scene

The last scene we will add in this part is the main scene. This scene will contain the gameplay, which is fine for a basic game.

{{<highlight js>}}
class SceneMain extends Phaser.Scene {
    constructor() {
        super({ key: "SceneMain" });
    }

    create() {

    }

    update() {

    }
}
{{</highlight>}}

## Game Configuration

The game configuration is what we use to define important properties of our game. Some of these properties include: rendering technology, width, height, background color, and the default physics system.

Add the following code to our game.js file:

{{<highlight js>}}
var config = {
    type: Phaser.WEBGL,
    width: 640,
    height: 640,
    backgroundColor: "black",
    physics: {
        default: "arcade",
        arcade: {
            gravity: { x: 0, y: 0 }
        }
    },
    scene: [
        SceneBoot,
        SceneMain
    ],
    pixelArt: true,
    roundPixels: true
};
{{</highlight>}}

## Creating a Game Instance

Now we&#8217;re at the easy part, defining the game instance. All we will be doing is assigning an instance of _Phaser.Game_ to a variable called _game_. We can pass in our game configuration object we made earlier so the properties we defined get applied. After the code for our game configuration, add:

{{<highlight js>}}
var game = new Phaser.Game(config);
{{</highlight>}}

## Concluding Thoughts

At this point we should see our game canvas appearing once we navigate to our project via localhost in the browser. To navigate to your game, type _localhost:<port>_/<directory>, with the port being the port your web server is serving to. Some web servers don&#8217;t require having to type in a specfic port number in. On my Linux machine running XAMPP, you can just type in &#8220;localhost/<directory>&#8221;. You can usually find the specific port for the web server you&#8217;re using by a quick search.

Hopefully this guide has been useful for you. If it has, please consider sharing this series on your favorite social media platform. Subscribe to our newsletter [here][2], to receive news regarding our latest tutorials and courses.

 [1]: https://learn.yorkcs.com/2019/09/25/phaser-3-basics-setup/
 [2]: https://yorkcs.activehosted.com/f/1