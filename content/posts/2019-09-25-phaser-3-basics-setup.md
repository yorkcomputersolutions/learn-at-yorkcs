---
title: 'Phaser 3 Basics: Setup'
author: Jared
type: post
date: 2019-09-25T21:35:27+00:00
url: /2019/09/25/phaser-3-basics-setup/
featured_image: /wp-content/uploads/2019/09/phaser-3-basics-setup-wp-square.png
rank_math_primary_category:
  - 297
rank_math_description:
  - "Learn how to setup a sample project to get started tinkering with Phaser 3. This bite-sized tutorial will ensure you're ready to hit the ground running."
rank_math_focus_keyword:
  - Phaser 3
rank_math_robots:
  - 'a:1:{i:0;s:5:"index";}'
rank_math_internal_links_processed:
  - 1
rank_math_analytic_object_id:
  - 27
categories:
  - Phaser 3
series:
  - Phaser 3 Basics
tags:
  - Phaser 3

---
This tutorial has been updated November, 2019.

In this part, we will setup an environment to create a Phaser 3 game.

Before we dive in, we need a web server of some sort in order to run our game. This is necessary because we don’t want any malicious JavaScript to read our file system from within the browser. Phaser’s website has a great [guide][1] on the web server portion of the setup.

## Adding Initial Files and Folders

Second, create a directory to house our project. The directory should be made in a location where the web server you installed can serve from. At this point, if you would like to use an NPM-based project template, you can jump skip this part of the tutorial and jump down to the heading, &#8220;Setting Up Phaser.&#8221; I go on to explain how to setup the template. You don&#8217;t need to create a folder here as you would be cloning a GitHub repository. Otherwise, we will proceed with creating a folder and our files manually.

If I’m using XAMPP or MAMP, I would create a folder in the htdocs directory. Other web servers may have different locations for serving files.<figure class="wp-block-image size-large">

<img loading="lazy" width="653" height="489" src="https://learn.yorkcs.com/wp-content/uploads/2019/11/phaser-3-basics-setup-created-base-dir.png" alt="" class="wp-image-11302" /> </figure> 

Then, create two files in our project directory: index.html and game.js. The .html and .js extensions are very important. The .html extension denotes an HTML file and the .js extension represents a JavaScript file. Create a folder for images of be used. Name it anything you wish, I usually name my folder for images pretty simply — images. Last, create a folder for sounds to be used as well. Like the images folder, name the sounds folder anything you like.<figure class="wp-block-image size-large">

<img loading="lazy" width="653" height="488" src="https://learn.yorkcs.com/wp-content/uploads/2019/11/phaser-3-basics-setup-manual-contents.png" alt="" class="wp-image-11301" /> </figure> 

Once our files are created and are in the proper places, we can open our _index.html_ file. Feel free to use any text or code editor you wish. Personally, I enjoy using [Visual Studio Code][2] since it&#8217;s clean, lightweight, and fast.

In the _index.html_ file, add the following boilerplate code:

<pre class="EnlighterJSRAW" data-enlighter-language="html" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">&lt;!DOCTYPE html>
    &lt;head>
        &lt;meta charset="utf-8">
        &lt;meta lang="en-us">
        &lt;title>My Awesome Game&lt;/title>
    &lt;/head>

    &lt;body>
        
    &lt;/body>
&lt;/html></pre>

What you would add to the _index.html_ file next depends on how you want to add the Phaser script. See below for the different options.

## Setting Up Phaser

### Linking via a CDN

Perhaps the fastest way to get started with Phaser is fetching the framework from a content delivery network (CDN). Photon Storm currently has [Phaser][3] hosted on the [jsDeliver][4] CDN. All you have to is add the following line to the body of your _index.html_ document.

<pre class="EnlighterJSRAW" data-enlighter-language="html" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">&lt;script src="//cdn.jsdelivr.net/npm/phaser@3.20.1/dist/phaser.js">&lt;/script></pre>

As of the time of updating this article (November of 2019), Phaser 3 version 3.20.1 is out. Of course to receive the latest version, you need the latest link. You can find the CDN link to the latest Phaser 3 version [here][5].

### Utilizing the Phaser 3 Project Template (NPM)

Phaser 3 games can also be made using a convenient project template built by Photon Storm! All you have to do, is ensure you have NodeJS/NPM installed, then clone this repository. Once you have cloned the repository, run _npm install_ from within the cloned directory. After that, just run _npm start_. You will be able to view your game at _localhost:8080_. If you are a regular NPM user (or even if you&#8217;re not), using the Phaser 3 Project Template can be a convenient option to get your game up and running.

### Using the Script File Locally

To download Phaser for local use, navigate to the Phaser 3 [GitHub repository][6]. Click the &#8220;dist&#8221; folder. We can pick one of two files to download: phaser.js, or phaser.min.js. The difference is that phaser.js contains a uncompressed version of the Phaser framework. This is useful for contributing to the project, and for checking implementation details. The file phaser.min.js is compressed and is meant for distributing your game. Either file will work for our purposes. To download a file, simply click on it and click “Download” or “Raw.” After that, right click the page with the code and click “Save Page As.” Save the file into the _js_ folder inside the project directory we made. Then, in our _index.html_ file, add the following line between the _<body>_ tags in order to link our script:

<pre class="EnlighterJSRAW" data-enlighter-language="html" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">&lt;script src="js/&lt;FILE NAME OF SCRIPT YOU DOWNLOADED>.js">&lt;/script></pre>

Obviously, you will need to replace the file name with the name of the script you downloaded, including the _.js_ file extension.

## Ready to Tinker with Phaser 3

Everything we need is setup and ready to go for our Phaser 3 project! You can find all the other parts of this series [here][7]. The next step would be to write the boilerplate code in [this tutorial][8]. If you like what you’ve read so far, consider subscribing to our [newsletter][9]. Our newsletter brings you the latest news regarding our tutorials and courses. Sharing this guide on social media would also be highly appreciated, of course only if you found it helpful.

 [1]: https://phaser.io/tutorials/getting-started-phaser3/part2
 [2]: https://code.visualstudio.com/
 [3]: https://phaser.io
 [4]: https://www.jsdelivr.com/
 [5]: https://phaser.io/download/stable
 [6]: https://github.com/photonstorm/phaser
 [7]: https://learn.yorkcs.com/category/phaser-3-basics/
 [8]: https://learn.yorkcs.com/2019/09/27/phaser-3-basics-boilerplate-code/
 [9]: https://learn.yorkcs.com/newsletter