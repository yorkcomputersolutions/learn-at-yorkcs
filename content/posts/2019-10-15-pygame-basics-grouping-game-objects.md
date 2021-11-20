---
title: 'PyGame Basics: Grouping Game Objects'
author: Jared
type: post
date: 2019-10-15T21:34:59+00:00
url: /2019/10/15/pygame-basics-grouping-game-objects/
featured_image: /wp-content/uploads/2019/10/pygame-basics-grouping-game-objects.png
rank_math_primary_category:
  - 315
rank_math_description:
  - Learn the importance and implementation of grouping game objects with PyGame! This bite-sized guide shows you everything you need to know to get started.
rank_math_focus_keyword:
  - grouping game objects with PyGame
rank_math_robots:
  - 'a:1:{i:0;s:5:"index";}'
rank_math_internal_links_processed:
  - 1
rank_math_analytic_object_id:
  - 9
categories:
  - PyGame
series:
  - PyGame Basics
tags:
  - game development
  - PyGame

---
In this guide, we will be taking a look at grouping game objects with [PyGame][1]. This is useful because most likely you will want to add or remove objects of the same type. Simply using variables to reference objects with won&#8217;t cut it. You might use a variable for assigning an instance of the player, but what if you want to add 20 enemies? Unless you name each one with a number after, it won&#8217;t work so well. Even if you name each enemy as a separate variable, that&#8217;s extremely inefficient. Not to mention, writing many separate variables to represent multiple of the same instance makes your code unmaintainable.

If you&#8217;ve been programming with Python for any length of time, you probably know what a list is. Well, if we&#8217;re developing a PyGame game, we can put them to good use. Lists are quite flexible, meaning we can add and remove items from them. There are two list methods we will focusing on: _append_ and _remove_.

Let&#8217;s say you have a list defined in the constructor of your game class.

<pre class="EnlighterJSRAW" data-enlighter-language="python" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">self.enemies = []</pre>

Now what if you wanted to add an enemy to this list? Assuming you are creating an instance of the enemy within your game class, you could write the following:

<pre class="EnlighterJSRAW" data-enlighter-language="python" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">new_enemy = MyEnemy((128, 128), enemy_image)</pre>

Then to add it to the list, you can type:

<pre class="EnlighterJSRAW" data-enlighter-language="python" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">self.enemies.append(new_enemy)</pre>

To update the enemies, you could write a for loop, iterating through the _enemies_ list.

<pre class="EnlighterJSRAW" data-enlighter-language="python" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">for enemy in self.enemies:
    enemy.update()</pre>

To remove enemies, you could have a boolean defined in the enemy class that determines whether the enemy should be removed or not. You can then test if it should be removed within the above for loop. The resulting for loop would look something like so:

<pre class="EnlighterJSRAW" data-enlighter-language="python" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">for enemy in self.enemies:
    if enemy.can_remove:
        self.enemies.remove(enemy)</pre>

The remove method takes in a reference to the instance you wish to remove from the array.

With the _append_ and _remove_ methods, you can almost do _anything!_ Well, pretty much. Being able to store instances in groups, in this case, lists, will really help you on your game development journey.

At this point, you know the importance of grouping game objects with PyGame, as well as the implementation details of doing so! As you develop, you will begin to realize how useful lists really are. If you found this tutorial useful, you may want to consider checking out the rest of this [tutorial series][2]. To receive updates regarding new tutorials and courses we publish, be sure to subscribe to our [newsletter][3]. If you found this guide valuable, consider sharing it on the social media platform of your choice.

 [1]: https://pygame.org
 [2]: https://learn.yorkcs.com/category/tutorials/gamedev/pygame/pygame-basics/
 [3]: https://learn.yorkcs.com/newsletter