---
title: Using TrueType Fonts with MonoGame
author: Jared
type: post
date: 2019-05-05T20:55:45+00:00
url: /2019/05/05/using-truetype-fonts-with-monogame/
featured_image: /wp-content/uploads/2019/05/monogame_spritefont_post_result.png
rank_math_internal_links_processed:
  - 1
rank_math_focus_keyword:
  - monogame
rank_math_seo_score:
  - 72
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
rank_math_schema_Article:
  - 'a:6:{s:5:"@type";s:11:"BlogPosting";s:8:"headline";s:11:"%seo_title%";s:13:"datePublished";s:20:"%date(Y-m-dTH:i:sP)%";s:12:"dateModified";s:24:"%modified(Y-m-dTH:i:sP)%";s:6:"author";a:2:{s:5:"@type";s:6:"Person";s:4:"name";s:5:"Jared";}s:8:"metadata";a:3:{s:5:"title";s:7:"Article";s:9:"isPrimary";b:1;s:4:"type";s:8:"template";}}'
rank_math_analytic_object_id:
  - 56
categories:
  - MonoGame

---
Today I was reading up on how to load TrueType fonts into MonoGame (version 3.7.1), but couldn&#8217;t get the TTF file to build with the MonoGame Pipeline Tool. In this tutorial, I will be covering my slight workaround in order to load TTF fonts into MonoGame.

First, create a new MonoGame project if you haven&#8217;t already. I chose the &#8220;MonoGame Cross Platform Desktop Project&#8221; template. The next thing I did was open the Content.mgcb file in the Content folder of my project with the MonoGame Pipeline Tool.

![](https://learn.yorkcs.com/wp-content/uploads/2019/05/monogame_pipeline_empty.png)

Click the &#8220;Add Existing&#8221; button on the top toolbar, then opened the TTF file I wanted to use. Once I clicked &#8220;Open,&#8221; another prompt appeared asking if I wanted to copy the file or link it. Make sure you choose copy the file, the click &#8220;OK&#8221;. Select the TTF file under the project pane, and change the build action from Build to Copy in the Properties pane. This is what allowed me to work around this build issues I was having. After that, you will want to right click the Content project under the project list (found in the pane on the left of the window). On the drop-down menu, go to Add > New Item&#8230; and click on that option. A new prompt will appear where you can type the name you want the SpriteFont to have. It does not need to be the same name as the TTF file. Ensure that &#8220;SpriteFont Description (.spritefont)&#8221; is chosen. Once you&#8217;re ready, click the &#8220;Create&#8221; button. The spritefont file should now be added to our project&#8217;s content pipeline. Now, we will have to right click our newly created spritefont file and choose &#8220;Open With&#8221;. Select a text or code editor of your choice and open the file. Between the _<FontName>_ tags in the spritefont file, add the file name of the TTF file you added including the .ttf extension. Feel free to adjust any other properties you need while you&#8217;re still in the spritefont file. Once you&#8217;re done, close out of your editor and head back to Visual Studio. At the top of your main game file, _Game1.cs_, under the declaration of the SpriteBatch, add the following line:

{{<highlight cs>}}
SpriteFont myFont; // Feel free to name "myFont" to anything else.
{{</highlight>}}

Once we&#8217;ve declared the SpriteFont, we will need to add it to our _LoadContent_ method. After the comment, &#8220;TODO: use this.Content to load your game content here,&#8221; add the following line:

{{<highlight cs>}}
myFont = Content.Load<SpriteFont>("myFont");
{{</highlight>}}

Now, let&#8217;s try drawing a string with our font! In the _Draw_ method, add the following code:

{{<highlight cs>}}
spriteBatch.Begin();
spriteBatch.DrawString(myFont, "Hello world!", new Vector2(32, 32), Color.White);
spriteBatch.End();
{{</highlight>}}

Note, if you have already added calls to _spriteBatch.Begin_ and _spriteBatch.End_, you don&#8217;t need to add them from the code above. When we go to run our game, we should now see something like the following:

![](https://learn.yorkcs.com/wp-content/uploads/2019/05/monogame_spritefont_post_result.png)

It works! Big thanks to [Reekee of Dimenzioned][1] on dafont.com for posting the awesome free font, Arcadepix! Even though I followed the MonoGame documentation for using TrueType fonts (which you can find [here][2]), the article doesn&#8217;t mention anything about setting the build action to Copy for the TTF file. Perhaps I&#8217;m missing something? I&#8217;m not sure. If anyone out there has a better/official solution, I would love to hear it! In the meantime, hopefully this guide will be able to help some of you out.

 [1]: https://www.dafont.com/reekee-of-dimenzioned.d1065
 [2]: http://www.monogame.net/documentation/?page=Using_TrueType_Fonts