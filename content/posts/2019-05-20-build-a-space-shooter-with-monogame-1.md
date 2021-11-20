---
title: Build a Space Shooter with MonoGame – 1
author: Jared
type: post
date: 2019-05-20T23:02:26+00:00
url: /2019/05/20/build-a-space-shooter-with-monogame-1/
featured_image: /wp-content/uploads/2019/05/build-space-shooter-monogame-1.jpg
rank_math_internal_links_processed:
  - 1
rank_math_primary_category:
  - 184
rank_math_seo_score:
  - 86
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
  - 50
categories:
  - MonoGame
series:
  - Build a Space Shooter with MonoGame
tags:
  - cross-platform
  - crossplatform
  - MonoGame

---
INTRODUCTION  


In this course, we will be creating a space shoot-em-up game with MonoGame! &nbsp;MonoGame is an open-source implementation of XNA, and has a very active community surrounding it. &nbsp;Before we get started, it will be important that you have MonoGame installed. If you need to install MonoGame on Windows, you can check out our installation [guide][1], otherwise the installers for other platforms should be similar. &nbsp;If you are using Mac OS or Linux, you can find the download links on this page (for version 3.7.1 as of May 4, 2019), [here][2].

SETTING UP THE PROJECT

The next thing we have to do is setup the project. &nbsp;In Visual Studio, select File > New > Project…  
<figure class="wp-block-image">

<img loading="lazy" width="1009" height="694" src="https://learn.yorkcs.com/wp-content/uploads/2019/05/new_project_menu-1.png" alt="" class="wp-image-1642" /> </figure> 

A new window should pop up allowing you to choose a project template. &nbsp;What we want to do is expand the _Visual C#_ dropdown on the left sidebar, then select “MonoGame Cross Platform Desktop Project.” &nbsp;This project template will tell MonoGame to use OpenGL meaning we can run the game on not only Windows, but also Mac and Linux! &nbsp;Your screen should now look similar to:  
<figure class="wp-block-image">

<img src="https://learn.yorkcs.com/wp-content/uploads/2019/05/select_project_type-1-1024x736.png" alt="" class="wp-image-1643" /> </figure> 

The next step is to name the project. &nbsp;To do this, you can fill out the text box next to the “Name” field on the bottom of this window. &nbsp;Don’t worry about the “Solution name” field, Visual Studio will fill this in for you. Once you’re ready, click the _OK_ button.  


For this course, we will also need to download the content for our game (images and sounds.) &nbsp;The content is freely available for download [here][3].  


In order to add our content to the game, we will have to provide it to the MonoGame Pipeline Tool to add it to our project. &nbsp;I would recommend expanding the Content folder of our project (within the Solution Explorer of Visual Studio), right click “Content.mgcb”, then click Open With… A new dialog should appear, where you can click on “MonoGame Pipeline Tool.” &nbsp;Once that option is selected, if I were you, I would set that option as default via the associated button.  


At this point, you should see the following in the “Open With” dialog:  
<figure class="wp-block-image">

<img loading="lazy" width="864" height="778" src="https://learn.yorkcs.com/wp-content/uploads/2019/05/set_monogame_pipeline_as_default-1.png" alt="" class="wp-image-1644" /> </figure> 

Once that’s all set, just click the _OK_ button, and you should be good to go! &nbsp;We can now add the content to our game. The first thing we’ll need to do now, is double click the “Content.mgcb” file in the Solution Explorer pane. &nbsp;Now the MonoGame Pipeline Tool should open since we’ve set it as the default application to open _.mgcb_ files.  
<figure class="wp-block-image">

<img src="https://learn.yorkcs.com/wp-content/uploads/2019/05/monogame_pipeline_empty-1-1024x803.png" alt="" class="wp-image-1645" /> </figure> 

You should see something like the above window once the pipeline tool has opened. 

Unfortunately, we won’t be able to just select our content, and drag and drop it in. &nbsp;So, we will have to click “Add Existing Item.” This button should be on the row of buttons at the top of the window:  
<figure class="wp-block-image">

<img src="https://learn.yorkcs.com/wp-content/uploads/2019/05/monogame_pipeline_add_existing_item-1-1024x812.png" alt="" class="wp-image-1646" /> </figure> 

An open dialog should now be displayed. &nbsp;The next step is to find the ZIP file you downloaded containing the content and extract it. &nbsp;Then, click on the newly extracted folder and select all the files like so:  
<figure class="wp-block-image">

<img src="https://learn.yorkcs.com/wp-content/uploads/2019/05/select_content-1-1024x800.png" alt="" class="wp-image-1647" /> </figure> 

Once you’ve selected all of the content, click the _Open_ button. &nbsp;If all goes right, you should now see another prompt on your screen asking you what you want to do:  
<figure class="wp-block-image">

<img loading="lazy" width="566" height="419" src="https://learn.yorkcs.com/wp-content/uploads/2019/05/monogame_pipeline_add_existing_what_to_do-1.png" alt="" class="wp-image-1648" srcset="https://learn.yorkcs.com/wp-content/uploads/2019/05/monogame_pipeline_add_existing_what_to_do-1.png 566w, https://learn.yorkcs.com/wp-content/uploads/2019/05/monogame_pipeline_add_existing_what_to_do-1-300x222.png 300w, https://learn.yorkcs.com/wp-content/uploads/2019/05/monogame_pipeline_add_existing_what_to_do-1-480x355.png 480w, https://learn.yorkcs.com/wp-content/uploads/2019/05/monogame_pipeline_add_existing_what_to_do-1-81x60.png 81w, https://learn.yorkcs.com/wp-content/uploads/2019/05/monogame_pipeline_add_existing_what_to_do-1-122x90.png 122w, https://learn.yorkcs.com/wp-content/uploads/2019/05/monogame_pipeline_add_existing_what_to_do-1-450x333.png 450w" sizes="(max-width: 566px) 100vw, 566px" /> </figure> 

Ensure the option, “Copy the file to the directory” is selected. &nbsp;I would also mark the checkbox labeled, “Use the same action for all the selected files.” &nbsp;After that, click _Add_ and the content should then be added to our project’s pipeline!  
<figure class="wp-block-image">

<img loading="lazy" width="996" height="738" src="https://learn.yorkcs.com/wp-content/uploads/2019/05/monogame_pipeline_files_added-1.png" alt="" class="wp-image-1649" /> </figure> 

Of course, we still can’t use it in our game yet. &nbsp;Let’s click the _Build_ button on the top of the pipeline tool and wait for our content to build.  
<figure class="wp-block-image">

<img src="https://learn.yorkcs.com/wp-content/uploads/2019/05/monogame_pipeline_content_built-1-1024x766.png" alt="" class="wp-image-1650" /> </figure> 

At this point, we can close the pipeline (for now). &nbsp;We will be coming back to it once we add text to our game. &nbsp;Let’s have a go at running the game and see what we get. At the top of Visual Studio, you should see the _Start_ button.  
<figure class="wp-block-image">

<img loading="lazy" width="617" height="255" src="https://learn.yorkcs.com/wp-content/uploads/2019/05/visual_studio_start_button-1.png" alt="" class="wp-image-1651" /> </figure> 

If we click the button, our game will compile and we should see the following:  
<figure class="wp-block-image">

<img src="https://learn.yorkcs.com/wp-content/uploads/2019/05/monogame_running_empty_game-1-1024x656.png" alt="" class="wp-image-1652" /> </figure> 

This looks pretty eventful, huh? &nbsp;We’ll spruce it up, but we have to get some of the more boring work out of the way first. &nbsp;This includes loading our content.

Let&#8217;s continue with [part two][4]!

 [1]: https://learn.yorkcs.com/2019/04/30/setting-up-monogame-on-windows/
 [2]: http://community.monogame.net/t/monogame-3-7-1-release/11173
 [3]: http://www.mediafire.com/file/yj5ozv5118b5548/BuildSpaceShooterMonoGameContent.zip/file
 [4]: https://learn.yorkcs.com/2019/05/20/build-a-space-shooter-with-monogame-2/