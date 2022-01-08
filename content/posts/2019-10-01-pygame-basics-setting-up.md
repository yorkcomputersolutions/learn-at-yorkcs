---
title: 'PyGame Basics: How to Setup PyGame'
author: Jared
type: post
date: 2019-10-01T16:42:22+00:00
url: /2019/10/01/pygame-basics-setting-up/
featured_image: /wp-content/uploads/2019/10/pygame-basics-2.png
rank_math_primary_category:
  - 315
rank_math_description:
  - Learn everything you need to get Python and PyGame setup. The goal of the PyGame Basics series is to teach you the fundamentals in an understandable way.
rank_math_focus_keyword:
  - setup PyGame
rank_math_robots:
  - 'a:1:{i:0;s:5:"index";}'
rank_math_seo_score:
  - 65
rank_math_internal_links_processed:
  - 1
rank_math_analytic_object_id:
  - 18
categories:
  - PyGame
series:
  - PyGame Basics
tags:
  - guide
  - Python
  - setup

---
Before we jump into building a game, we will need to setup PyGame. Since PyGame requires Python, we will need to ensure it&#8217;s installed first. This tutorial series assumes you will be using Python 3. You can download and install Python 3 from the [official website][1].

## Installing PyGame

_If you&#8217;re running Linux, ensure the python3-pip package is installed._

Once you have Python installed, we can setup [PyGame][2]. Open your command prompt or terminal and run:

<pre class="wp-block-preformatted"><em>pip3 install pygame</em></pre>

This command should install everything we need to get started with PyGame. If you&#8217;re having issues with the installation, I would recommend taking a look at the [Getting Started][3] guide on the PyGame website.

![](https://learn.yorkcs.com/wp-content/uploads/2019/10/Screenshot_20191001_115409.png)

## Creating a Project Directory and File

Next, create a folder for your project. Find the location where you want to store your project, and make a folder there. Name the folder anything you like. Enter the folder, then create a new file. I&#8217;m going to name mine _game.py_, though you can name yours whatever you wish. Make sure the file extension is _.py_ though. The _.py_ file extension indicates a Python file. This is important when we go to run the script. For the purposes of this series, I&#8217;ll refer to this main file as _game.py_. Open our _game.py_ script with your favorite text/code editor. Personally, I love Visual Studio Code for easy debugging and code completion. If you&#8217;re using another editor, I&#8217;ll explain how to run your project via the command line. Once you&#8217;ve opened the _game.py_ file, add the following:

{{<highlight py3>}}
import pygame

pygame.init()
{{</highlight>}}

## Running the Game

To run the game, ensure you&#8217;re in our project directory in the command line. Then, type _python3 game.py_. The game should then compile to bytecode and be interpreted. It&#8217;s worth noting if you&#8217;re using Visual Studio Code, you can go to Debug > Start Debugging to use the Python debugger instead of running the script with Python via the terminal.

## Concluding Thoughts

At this point, we have a basic PyGame set up! If you found this guide useful, you would probably find the [rest of this series][4] helpful too. You can receive news about our latest tutorials and courses we publish, you can subscribe to our newsletter. If you found this tutorial helpful, and would like to help us out, sharing this guide on your favorite social media platform would be appreciated.

 [1]: https://www.python.org/downloads/
 [2]: https://pygame.org
 [3]: https://www.pygame.org/wiki/GettingStarted
 [4]: https://learn.yorkcs.com/category/tutorials/gamedev/pygame/pygame-basics/