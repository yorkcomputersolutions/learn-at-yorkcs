---
title: Build a Space Shooter with MonoGame – 2
author: Jared
type: post
date: 2019-05-20T23:02:32+00:00
url: /2019/05/20/build-a-space-shooter-with-monogame-2/
featured_image: /wp-content/uploads/2019/05/build-space-shooter-monogame-1.jpg
rank_math_internal_links_processed:
  - 1
rank_math_primary_category:
  - 184
rank_math_seo_score:
  - 71
rank_math_robots:
  - 'a:1:{i:0;s:5:"index";}'
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
  - monogame
rank_math_schema_Article:
  - 'a:6:{s:5:"@type";s:11:"BlogPosting";s:8:"headline";s:11:"%seo_title%";s:13:"datePublished";s:20:"%date(Y-m-dTH:i:sP)%";s:12:"dateModified";s:24:"%modified(Y-m-dTH:i:sP)%";s:6:"author";a:2:{s:5:"@type";s:6:"Person";s:4:"name";s:5:"Jared";}s:8:"metadata";a:3:{s:5:"title";s:7:"Article";s:9:"isPrimary";b:1;s:4:"type";s:8:"template";}}'
rank_math_analytic_object_id:
  - 49
categories:
  - MonoGame
series:
  - Build a Space Shooter with MonoGame
tags:
  - 'C#'
  - 'C# game'
  - cross-platform
  - crossplatform
  - csharp
  - Microsoft
  - space shooter
  - spaceshooter
  - xna

---
If _Game1.cs_ is not already open in your code window, you can navigate to it via the Solution Explorer. &nbsp;Once _Game1.cs_ is displayed, add the following to the _using_ statements at the top:  


using Microsoft.Xna.Framework.Audio;

using System.Collections.Generic;

using System;  


We will need the audio part of MonoGame in order to load and play our sounds. &nbsp;We also specify that we want to use “System.Collections.Generic”. We will need this to create lists to hold objects in our game. &nbsp;We will be using “System” for randomly generating numbers. Before we get too ahead of ourselves, let’s define the fields we’ll use for referencing our images (textures). &nbsp;Add the following under the _SpriteBatch_ definition, “SpriteBatch spriteBatch;”:  


{{<highlight cs>}}
private List<Texture2D> texBgs = new List<Texture2D>();
private Texture2D texBtnPlay;
private Texture2D texBtnPlayDown;
private Texture2D texBtnPlayHover;
private Texture2D texBtnRestart;
private Texture2D texBtnRestartDown;
private Texture2D texBtnRestartHover;
private Texture2D texPlayer;
private Texture2D texPlayerLaser;
private Texture2D texEnemyLaser;
private List<Texture2D> texEnemies = new List<Texture2D>();
private Texture2D texExplosion;

public SoundEffect sndBtnDown;
public SoundEffect sndBtnOver;
public List<SoundEffect> sndExplode = new List<SoundEffect>();
public SoundEffect sndLaser;

private SpriteFont fontArial;
{{</highlight>}}

From this point on, I will be calling the images we’ve added to our pipeline as textures. &nbsp;When we reference textures in our code, they will be the correct type, “Texture2D”. This is very important. &nbsp;Notice how all of the texture fields are _private_. &nbsp;We won’t be accessing these fields from within other classes, so we don’t have to bother making them public.  


In order to grab the textures and sounds from our project’s pipeline, we will have to interface with the _ContentManager_, which allows MonoGame to interact with the pipeline. &nbsp;In our case, we will be using the _Load_ method of the ContentManager, which we can access using the _Content_ instance. &nbsp;This might sound pretty confusing. &nbsp;No worries though, we will simply be loading our content like so:  


<field name> = Content.Load<Texture2D>(“filename without extension”);  


Not too bad, right? &nbsp;We will be loading our sound effects and SpriteFonts (our game’s font(s)) quite similarly, but instead of using the _Texture2D_ class, we will utilize _SoundEffect_ and _SpriteFont_. &nbsp;Let’s put this into practice! &nbsp;In the _LoadContent_ method, right under the line:

// TODO: use this.Content to load your game content here

{{<highlight cs>}}
// Load textures

for (int i = 0; i < 2; i++)
{
	texBgs.Add(Content.Load<Texture2D>("sprBg" + i));
}

texBtnPlay = Content.Load<Texture2D>("sprBtnPlay");
texBtnPlayDown = Content.Load<Texture2D>("sprBtnPlayDown");
texBtnPlayHover = Content.Load<Texture2D>("sprBtnPlayHover");

texBtnRestart = Content.Load<Texture2D>("sprBtnRestart");
texBtnRestartDown = Content.Load<Texture2D>("sprBtnRestartDown");
texBtnRestartHover = Content.Load<Texture2D>("sprBtnRestartHover");

texPlayer = Content.Load<Texture2D>("sprPlayer");
texPlayerLaser = Content.Load<Texture2D>("sprLaserPlayer");
texEnemyLaser = Content.Load<Texture2D>("sprLaserEnemy0");

for (int i = 0; i < 3; i++)
{
	texEnemies.Add(Content.Load<Texture2D>("sprEnemy" + i));
}

texExplosion = Content.Load<Texture2D>("sprExplosion");
{{</highlight>}}

As I mentioned before, we can load our sounds in the same way. &nbsp;Add the following:

{{<highlight cs>}}
// Load sounds
sndBtnDown = Content.Load<SoundEffect>("sndBtnDown");
sndBtnOver = Content.Load<SoundEffect>("sndBtnOver");
for (int i = 0; i < 2; i++)
{
	sndExplode.Add(Content.Load<SoundEffect>("sndExplode" + i));
}
sndLaser = Content.Load<SoundEffect>("sndLaser");
{{</highlight>}}

Plus, we can load our single sprite font similarly:

{{<highlight cs>}}
// Load sprite fonts

fontArial = Content.Load<SpriteFont>("arialHeading");
{{</highlight>}}


If we run the game now, we’ll see an error claiming ‘arialHeading’ does not exist. &nbsp;This is where sprite fonts come into play. Let’s open up the content pipeline for our project, and click the “New Item” button in the toolbar. &nbsp;  
<figure class="wp-block-image">

<img src="https://learn.yorkcs.com/wp-content/uploads/2019/05/monogame_pipeline_add_new_item-1-1024x777.png" alt="" class="wp-image-1656" /> </figure> 

A popup window should appear prompting you to name and select the type of file you wish to add. &nbsp;Choose “SpriteFont Description (.spritefont),” and name the file, “arialHeading”.  
<figure class="wp-block-image">

<img loading="lazy" width="993" height="740" src="https://learn.yorkcs.com/wp-content/uploads/2019/05/monogame_pipeline_spritefont_selected-2.png" alt="" class="wp-image-1657" /> </figure> 

Once you’ve selected the SpriteFont option, and named the file “fontArial,” we can click the _Create_ button. &nbsp;Our new SpriteFont file will be added to our project list. &nbsp;We will want to increase the font size though, since this font will be utilized for our title. &nbsp;Right click “arialHeading.spritefont” in our pipeline project, then click “Open With”. Choose a text editor or code editor of your choice, anything works. &nbsp;Then click _OK_ or the equivalent on your operating system, and the file should open in the editor you chose. &nbsp;I myself has chosen to use Visual Studio Code, which is a fantastic, fast code editor. At this point we should be seeing the following text:  
<figure class="wp-block-image">

<img src="https://learn.yorkcs.com/wp-content/uploads/2019/05/spritefont_def-1-769x1024.png" alt="" class="wp-image-1658" /> </figure> 

Change the value between the _<Size>_ tags from _12_ to _32_. &nbsp;We can also change the value of the _<Style>_ element to _Bold_. &nbsp;Save this file, and exit out of the editor you were using and let’s go back to the pipeline tool. &nbsp;

Build the pipeline project, then let’s head back to _Game1.cs_ in Visual Studio.

Now let&#8217;s keep going with [part three][1].

 [1]: https://learn.yorkcs.com/2019/05/20/build-a-space-shooter-with-monogame-3/