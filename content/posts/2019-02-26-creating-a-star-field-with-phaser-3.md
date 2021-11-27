---
title: Creating a “Center to Edge” Starfield with Phaser 3
author: Jared
type: post
date: 2019-02-26T19:02:12+00:00
url: /2019/02/26/creating-a-star-field-with-phaser-3/
featured_image: /wp-content/uploads/2019/02/starfieldcentertoedge_smaller.gif
rank_math_internal_links_processed:
  - 1
rank_math_seo_score:
  - 27
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
rank_math_robots:
  - 'a:1:{i:0;s:5:"index";}'
rank_math_schema_Article:
  - 'a:6:{s:5:"@type";s:11:"BlogPosting";s:8:"headline";s:11:"%seo_title%";s:13:"datePublished";s:20:"%date(Y-m-dTH:i:sP)%";s:12:"dateModified";s:24:"%modified(Y-m-dTH:i:sP)%";s:6:"author";a:2:{s:5:"@type";s:6:"Person";s:4:"name";s:5:"Jared";}s:8:"metadata";a:3:{s:5:"title";s:7:"Article";s:9:"isPrimary";b:1;s:4:"type";s:8:"template";}}'
rank_math_analytic_object_id:
  - 67
categories:
  - Phaser 3

---
In this tutorial, we will be creating what I call, a &#8220;center to edge&#8221; starfield. The final result will look like the following:<figure class="wp-block-image">

<img loading="lazy" width="640" height="640" src="https://learn.yorkcs.com/wp-content/uploads/2019/02/starfield_edgetoedge.gif" alt="" class="wp-image-828" /> </figure> 

#### Tutorial Requirements

  * Basic to intermediate knowledge of JavaScript
  * Web server
  * Code editor (not necessarily required, but highly recommended)

## Ensure a Web Server is Set Up

Even though Phaser games are ran in the browser, unfortunately you can&#8217;t just run local HTML files directly from your file system. When requesting files over http, the server security only allows you to access files you&#8217;re allowed to. When loading a file from the local file system (the file:// protocol), your browser highly restricts it for obvious security reasons. It&#8217;s not good to allow code on a website to read anything in your raw file system. Because of this, we will need to host our game on a local web server.

We recommend taking a look at Phaser&#8217;s official guide, &#8220;Getting Started with Phaser 3&#8221;, to learn which web server is compatible with your system and there are links to each one. The guide also provides some detailed summaries on each of the various web servers mentioned.

## Create the Folders and Files Needed

First, find the directory where your web server serves files from (WAMP Server, for example, hosts files from the www directory within it&#8217;s installation folder at C:/wamp64.) Once you have found the location, create a new folder inside it and call it anything you like.

Next, enter the folder and create a new file named, &#8220;index.html&#8221;. Our index file is where we will declare the location of our game scripts and Phaser script.

We will also need to create a folder inside our game folder for our JavaScript. This folder can be named anything you like, but we will be using it for storing our JavaScript. Once we have our folder for JavaScript, create two new files inside this folder named: game.js, and SceneMain.js.

The file structure of our project should look like so:

<pre class="wp-block-preformatted">(game folder)/<br />|_index.html<br />|_js/<br />    |_ game.js<br />    |_ SceneMain.js</pre>

The last step we have to do is grabbing the latest Phaser script from [GitHub][1]. For our purposes, feel free to click either, &#8220;phaser.js&#8221; or &#8220;phaser.min.js&#8221;. I personally chose &#8220;phaser.js&#8221;. Click the link for either script, and you should see a new page that displays a button named, &#8220;View raw&#8221;, near the center of the page, about halfway down. Next, click the &#8220;View raw&#8221; link, then right click anywhere on the new page of code that appears. Once the dropdown appears, click &#8220;Save Page As&#8221; or something similar. A save dialog should then appear where you can save the Phaser script in the JavaScript directory we created.

Let&#8217;s start by adding to our index.html file. Add the following code to create the HTML document and link our scripts:

{{<highlight html>}}
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <meta lang="en-us">
        <title>TutorialStarfield</title>
    </head>

    <body>
        <script src="js/phaser.js"></script>
        <script src="js/SceneMain.js"></script>
        <script src="js/game.js"></script>
    </body>
</html>
{{</highlight>}}

We are now finished with index.html. Moving on to game.js, add the following the file:

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
        SceneMain
    ],
    pixelArt: true,
    roundPixels: true
};
var game = new Phaser.Game(config);
{{</highlight>}}

The above code defines the configuration properties needed for creating the Phaser game. Feel free to play around with these.

Jumping to our SceneMain.js file, we can create the class for our scene, SceneMain. It&#8217;s good to point out that classes in JavaScript aren&#8217;t true classes. Classes are objects, but with some syntactic sugar sprinkled on top to make organizing object-oriented code easier. We will want our class to extend Phaser.Scene since we are going to be building on-top of the default Phaser.Scene object. Add the following to SceneMain.js:

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

The create function will be triggered as soon as the scene is started. We will want to add some properties, as well as generate the points for our stars there. In the create function, add the following properties:

{{<highlight js>}}
this.points = [];
this.stars = this.add.group();

this.maxDepth = 32;
{{</highlight>}}

Our star field will work by having an array of points, and a group for the graphics objects (the circles drawn). Each point will have three properties: x, y, and z. Positions x and y will determine where on the screen a star graphics object will be created, and z is used calculating how close a star is to the &#8220;observer&#8221;. The property maxDepth will be used for determining the maximum distance a star can be from the &#8220;observer&#8221;. Next, we will need to create a for loop which will create the point objects and add them to the points array:

{{<highlight js>}}
for (var i = 0; i < 512; i++) {
    this.points.push({
        x: Phaser.Math.Between(-25, 25),
        y: Phaser.Math.Between(-25, 25),
        z: Phaser.Math.Between(1, this.maxDepth)
    });
}
{{</highlight>}}

The last thing we need to do to make our star field work, is add some code to the update function of SceneMain. We will be clearing the stars each update, iterate through our points to calculate the new star positions, as well as create the star graphics objects at those positions. We will first start by adding some code to clear the stars group and also create a for loop to iterate through our points:

{{<highlight js>}}
this.stars.clear(true, true);

for (var i = 0; i < this.points.length; i++) {
    var point = this.points[i];
    
}
{{</highlight>}}

In addition to calculating the new position of each point, we will also be resetting the position once it gets close enough to the &#8220;observer&#8221;. This will save us from having to destroy and create new points. Add the following code inside the for loop to subtract from the z position of each point (which results in the star moving closer to the &#8220;observer&#8221; as z nears zero):

{{<highlight js>}}
point.z -= 0.2;
{{</highlight>}}

After that, we will also need to add the reset logic I mentioned above:

{{<highlight js>}}
if (point.z <= 0) {
    point.x = Phaser.Math.Between(-25, 25);
    point.y = Phaser.Math.Between(-25, 25);
    point.z = this.maxDepth;
}
{{</highlight>}}

Now that we&#8217;ve added the reset logic, we can calculate the new position of the current point. Add the following:

{{<highlight js>}}
var px = point.x * (128 / point.z) + (this.game.config.width * 0.5);
var py = point.y * (128 / point.z) + (this.game.config.height * 0.5);
{{</highlight>}}

The last thing we have to do is create the physical circle that will be drawn to represent a star. We will be creating an instance of Phaser&#8217;s circle object. This instance will act pretty much as a template to provide to an instance of Phaser&#8217;s graphics object to draw. After the previous code, add the following to create a circle at the position of the point:

{{<highlight js>}}
var circle = new Phaser.Geom.Circle(
    px,
    py,
    (1 - point.z / 32) * 2
);
{{</highlight>}}

The cool thing about the last parameter we added when creating our circle, is that it will grow in size as it nears the &#8220;observer&#8221;. Now, we can create the graphics object, and add it to the stars group. Add the following:

{{<highlight js>}}
var graphics = this.add.graphics({ fillStyle: { color: 0xffffff } });
graphics.setAlpha((1 - point.z / 32));
graphics.fillCircleShape(circle);
this.stars.add(graphics);
{{</highlight>}}

By setting the alpha, we can make stars in the distance much more faint, and have them become brighter as they near the &#8220;observer&#8221;.

If we navigate to the project in our browser, we should see finished result:<figure class="wp-block-image">

<img loading="lazy" width="640" height="640" src="https://learn.yorkcs.com/wp-content/uploads/2019/02/starfield_edgetoedge.gif" alt="" class="wp-image-828" /> <figcaption>Got it? Fantastic!</figcaption></figure> 

The fun part now is to tweak the various numbers. Some interesting results can be achieved! I look forward to seeing what you can create with this! Hopefully this will be useful for some of you. 🙂

You can find the full source code for this tutorial on [GitHub][4].

If you&#8217;re interested in hearing about more of my tutorials and courses, be sure to fill out the [form][5].

 [1]: https://github.com/photonstorm/phaser/tree/master/dist
 [2]: https://twitter.com/jaredyork_
 [3]: mailto://jared.york@jaredyork.com
 [4]: https://github.com/jaredyork/TutorialStarfieldCE
 [5]: https://docs.google.com/forms/d/e/1FAIpQLSfSAg6xMDrk44pbmIlVUqLwjm9FHaKPdy_WcbHUmLWWyXMQag/viewform?usp=sf_link