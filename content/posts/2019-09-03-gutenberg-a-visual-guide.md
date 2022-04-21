---
title: 'Gutenberg: A Visual Guide'
author: Jared
type: post
date: 2019-09-03T19:38:29+00:00
url: /2019/09/03/gutenberg-a-visual-guide/
featured_image: /wp-content/uploads/2019/08/gutenberg-1024.png
rank_math_internal_links_processed:
  - 1
rank_math_primary_category:
  - 270
rank_math_seo_score:
  - 88
rank_math_robots:
  - 'a:1:{i:0;s:5:"index";}'
rank_math_rich_snippet:
  - article
rank_math_snippet_shortcode:
  - '[rank_math_rich_snippet]'
rank_math_snippet_article_type:
  - BlogPosting
rank_math_snippet_book_editions:
  - 'a:1:{i:0;a:1:{s:11:"book_format";s:9:"Hardcover";}}'
rank_math_snippet_course_provider_type:
  - Organization
rank_math_snippet_event_type:
  - Event
rank_math_snippet_event_performer_type:
  - Person
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
  - Gutenberg
enclosure:
  - |
    |
        https://learn.yorkcs.com/wp-content/uploads/2019/08/A8C3B380-62CA-4780-839C-9B65204C793C.mov
        6507267
        video/quicktime
        
  - |
    |
        https://learn.yorkcs.com/wp-content/uploads/2019/08/4985991A-95B5-46C6-9879-B6BFC1253099.mov
        4607756
        video/quicktime
        
rank_math_description:
  - Dive into using the Gutenberg editor for WordPress! This guide explains the ins and outs of Gutenberg in one in-depth visual package.
rank_math_schema_Article:
  - 'a:7:{s:5:"@type";s:11:"BlogPosting";s:8:"headline";s:11:"%seo_title%";s:13:"datePublished";s:20:"%date(Y-m-dTH:i:sP)%";s:12:"dateModified";s:24:"%modified(Y-m-dTH:i:sP)%";s:6:"author";a:2:{s:5:"@type";s:6:"Person";s:4:"name";s:5:"Jared";}s:11:"description";s:133:"Dive into using the Gutenberg editor for WordPress! This guide explains the ins and outs of Gutenberg in one in-depth visual package.";s:8:"metadata";a:3:{s:5:"title";s:7:"Article";s:9:"isPrimary";b:1;s:4:"type";s:8:"template";}}'
rank_math_analytic_object_id:
  - 32
categories:
  - WordPress
tags:
  - editor
  - Gutenberg
  - page builder
  - webdesign
  - webdev
  - WordPress

---
The rise of the Gutenberg editor is in full swing, for better or worse. Gutenberg was introduced by Matt Mullenweg at&nbsp;[WordCamp Europe in 2017][1]. The editor was created to simplify website layouts, while attempting to make the task more user-friendly. While Gutenberg was originally a plugin, in December 2018, the editor was merged into WordPress Core with version 5.0. There is no doubt that Gutenberg is most likely being pushed to compete with page builder services such as Wix and Squarespace.

![](https://learn.yorkcs.com/wp-content/uploads/2019/08/A886B132-7415-4D3F-A153-6757EC226AEF.jpeg)

The traditional WordPress editor can still be used via installing the Classic Editor plugin. This plugin will continue to be supported until December 31, 2021, or as long as the need is there. In [this page on WordPress.org](https://make.wordpress.org/core/2018/11/07/classic-editor-plugin-support-window/), Automattic addresses additional support with:

> In 2021 we will evaluate continuing maintenance of the plugin, based on usage. We expect continued maintenance to be fairly trivial.
>
> Gary Pendergast (Automattic)

![The traditional editor can still be installed via the plugin directory, which can be found under, "Classic Editor."](https://learn.yorkcs.com/wp-content/uploads/2019/08/FF134C4B-0EC9-4DF6-9EE1-7785E3E1F6A0.jpeg)

But you probably weren&#8217;t here to learn about support timelines, rather, to learn how to use Gutenberg. So without further ado, let&#8217;s dive in!

## Block Basics

Blocks are the meat and potatoes of Gutenberg. They are the various elements on your website. Here is a small list of various blocks given to you:

  * Paragraphs
  * Headings
  * Images and Videos
  * Columns
  * And much more&#8230;

So let’s get started by creating our first post using Gutenberg. Select the “Add New” fro the Posts drop down, or alternatively, you can add a post via the “All Posts” page.

![](https://learn.yorkcs.com/wp-content/uploads/2019/08/4E5835B0-F7F6-48C2-B693-1B717519C44F.jpeg)

Right. Now you should see the following view for us to start putting our post together.

![](https://learn.yorkcs.com/wp-content/uploads/2019/08/4E163610-E1A5-40E2-B674-71717A6FB1D4 "This screenshot shows the editor view for the post we will be writing.")

From first glance, everything may seem pretty straight forward. You see where you can add the title, as well as where you can start typing. Let’s start by adding the most obvious choice for a title for our purposes. Simply click (or press, I’m using an iPad as I type this) and type your title.

![This photo shows the editor layout after we added a title.](https://learn.yorkcs.com/wp-content/uploads/2019/08/2AC1D024-C9A0-4497-A464-0F985366B6E8)

### Paragraphs

Next, we can click the label, “Start writing or type / to choose a block.” By default, Gutenberg will default to adding the text you type to a paragraph block. Feel free to type anything you like in the box.

![This screenshot shows some sample text inside the default paragraph block.](https://learn.yorkcs.com/wp-content/uploads/2019/08/DD54CFFA-A3D7-4982-882F-B9B48D191A54.png)

You may notice the options we have in the toolbar above the block we have in focus. There are quite a few buttons in the toolbar that you will find familiar, such as alignment, font wight, font style, as well as a link button. On the far left of the toolbar, you may notice the button with a paragraph symbol. This button allows you to change the current block to a different type of block.

![This screenshot shows the various blocks that you can change the selected block to.](https://learn.yorkcs.com/wp-content/uploads/2019/08/68708419-E8F1-47F1-B3F1-7A804D714281.jpeg)

### Images

When you’re done typing in the paragraph block, you might be wondering how to add a new block. On a desktop or laptop, you should see a plus button appear under the current block, if you move your mouse slightly under the block. Once you see the button appear, a new block will be added. On tablets, you may have to press return at the end of the last block to add a new block. New blocks can also be added via the plus button on the left side of the top toolbar.

![This photo shows that you can add more blocks to your post/page.](https://learn.yorkcs.com/wp-content/uploads/2019/08/C7FCF226-E959-4D40-A46E-AF5F0087E4CA.png)

Let’s change our new block into an image block. Click the plus button on the left side of the block and then select “Image.”

![This screenshot shows the various blocks we have at our disposal.](https://learn.yorkcs.com/wp-content/uploads/2019/08/B18F0629-5FF3-488E-B39C-B3B982C6988D.jpeg)

![This screenshot shows the various media options you have for an image block.](https://learn.yorkcs.com/wp-content/uploads/2019/08/BC113B20-227A-42F9-8633-E901E3B9DFF1.png)

At this point you can choose to either upload a new image, open your media library, or insert an image from a URL. Blocks have their own unique options depending on the type, which are displayed in the toolbar.

### Columns

There are also blocks that affect the layout of the current post/page. Let’s try one of these blocks, namely the “Columns” block. This block allows you to add blocks within, well, columns.
{{< video src="https://learn.yorkcs.com/wp-content/uploads/2019/08/A8C3B380-62CA-4780-839C-9B65204C793C.mp4" type="video/mp4" >}}

Once you have our new columns block added, we can add content to each column. Before we do however, it’s important to point out that you can change the number of columns using the sidebar on the right side of the editor. It can be _very_ difficult to select the columns block since there’s no way to tell which block you’re trying to select. Unfortunately, it’s necessary to select the block but all will be well once it is.
{{< video src="https://learn.yorkcs.com/wp-content/uploads/2019/08/4985991A-95B5-46C6-9879-B6BFC1253099.mp4" type="video/mp4" >}}

Once you’ve been finally got the block selected, you can change the number of columns via the slider.

At this point, we can select a block to put in each of our columns. For my paragraph blocks, I will be adding some sample text.
![Here we added a block to each of our columns.](https://learn.yorkcs.com/wp-content/uploads/2019/09/CDDA8D7F-7BFA-46B2-8C28-157C0BFBB54A.png)

More blocks can be added to columns too! For example, we could add another image under our paragraph block in the left column.
![](https://learn.yorkcs.com/wp-content/uploads/2019/09/D7A25484-6DCB-4BF5-975C-166CF6565BC4.png)

## Taking a Look Around the Editor

### The Top Toolbar

Earlier I briefly mentioned the top toolbar. It’s worth noting there are a handful of useful tasks we can perform from this bar. Starting from the left, we have the add block button, next there are undo and redo buttons. After that, the next button is a bit interesting. It provides us information about the current document. These stats include your word count, amount of headings, paragraph count, and number of blocks.

![This screenshot shows the various stats related to this post/page.](https://learn.yorkcs.com/wp-content/uploads/2019/08/FEE92A90-8AD2-4137-9482-5B3B9DDA4AD8.png)

Finally, the last button on the left side of the top bar displays an ordered list of the blocks you’ve added.

![This is a photo showing the list of blocks utilized by your post/page.](https://learn.yorkcs.com/wp-content/uploads/2019/08/7FFDF54D-A325-41FD-82C2-6DEA54035314.png)

Moving along to the right side, we can see there’s a “Save Draft” button. It’s pretty self-explanatory. Then there is the preview, which allows us to take a look at how our post or page will appear live. Let’s generate a preview of our post.

![We can generate a preview of our post or page.](https://learn.yorkcs.com/wp-content/uploads/2019/09/C49675E0-30A4-4977-AA4F-60DA523DD41D.png)

The “Publish&#8230;” button well&#8230; publishes our post. The next button looks like a gear. If you see the right sidebar, this button should be darkened since it’s enabled. The gear button toggles the visibility of the right sidebar. Some plugins may also add other buttons to the top toolbar such as Yoast (hence the “Y” stylized button next to the right sidebar button. The last button, with the three vertical dots, allows you to access other options.

![The button with the three dots allows us to access more editor options.](https://learn.yorkcs.com/wp-content/uploads/2019/09/997D987E-3AF5-44B4-9524-94D0CE5241C3.png)

### Editor Views

If we take a look at the drop down menu under the three dot button, we should see options for three different views.

![We can view the editor three different ways.](https://learn.yorkcs.com/wp-content/uploads/2019/09/7299D5BF-758C-4B96-A5E8-B41BA43F2FAA.jpeg)

By default, Gutenberg places us in the _Top Toolbar View_. This view displays the top toolbar, as well as the document tools for our post. _Spotlight Mode_ lightens any block other than the active block, so it’s easier to focus.

![Spotlight Mode lightens other blocks, so you can focus on the current block.](https://learn.yorkcs.com/wp-content/uploads/2019/09/8F59D8A3-D8FF-43B5-92D8-D1C9EA82F28D.png)

The last view we can select is _Fullscreen Mode_. This view gives us a much cleaner editing layout.

![Fullscreen Mode gets rid of the clutter you don't need on screen.](https://learn.yorkcs.com/wp-content/uploads/2019/09/5FA2E54D-F627-4423-BBF8-580AB28D6EA8.png)

The neat thing is that multiple views can be enabled at the same time. For example, we can have Spotlight Mode and Fullscreen Mode active concurrently.

### The Right Sidebar

Block settings, like we&#8217;ve demonstrated above, can be accessed via the &#8220;Block&#8221; tab of the right sidebar. Some blocks have various options you can set. After selecting a block, you can view the settings for the block via the block tab. If you don&#8217;t see any options for a block after selecting one, ensure the Block tab is selected.

![Settings for a selected block can be changed via the "Block" tab.](https://learn.yorkcs.com/wp-content/uploads/2019/09/Screenshot-from-2019-09-03-15-00-54)

If we select the &#8220;Document&#8221; tab, we can change the main properties of our post.

![Document settings can be changed under the "Document" tab of the right sidebar.](https://learn.yorkcs.com/wp-content/uploads/2019/09/Screenshot-from-2019-09-03-15-01-06.png)

Under the &#8220;Status & Visibility&#8221; section, there are more dropdowns relating to permalinks, the featured image, the excerpt, etc. These settings are trivial to edit, you just have to click on the dropdown, and the option(s) should be there. When you are done making changes, click &#8220;Save Draft&#8221; if you don&#8217;t want to publish your post yet. Otherwise, when you wish to publish your post, you can click the &#8220;Publish&#8230;&#8221; button.

## Wrapping Up

In this guide, we put together our first post using the Gutenberg editor. While feelings are mixed regarding this new editor, there&#8217;s no doubt that it will continue to be pushed as the de-facto method to edit content. Gutenberg is much different from the traditional WordPress editor in many ways, but also similar in some. As the editor continues to mature, more users will migrate to Gutenberg. It is my hope that this guide has been useful. There is definitely a steeper learning curve, which I think justifies a more visual guide.

If you found this tutorial helpful, and would like to receive news of our latest tutorials and courses, please subscribe to our [newsletter][2]. We also write IT and computer science related courses, which are available in our [store][3].

 [1]: https://wordpress.tv/2017/07/01/interview-and-qanda-with-matt-mullenweg/
 [2]: https://yorkcs.activehosted.com/f/1
 [3]: https://learn.yorkcs.com/shop/