---
title: Linux Terminal Basics – Navigating the File System
author: Jared
type: post
date: 2019-07-03T18:23:01+00:00
url: /2019/07/03/linux-terminal-basics-navigating-the-file-system/
featured_image: /wp-content/uploads/2019/07/series-thumb-navigating-file-system-square-1.png
rank_math_internal_links_processed:
  - 1
rank_math_seo_score:
  - 80
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
  - terminal
rank_math_description:
  - Learn how to navigate the Linux filesystem using the Linux terminal. This guide will get you on the fast track to leveling up your Linux skills.
rank_math_schema_Article:
  - 'a:7:{s:5:"@type";s:11:"BlogPosting";s:8:"headline";s:11:"%seo_title%";s:13:"datePublished";s:20:"%date(Y-m-dTH:i:sP)%";s:12:"dateModified";s:24:"%modified(Y-m-dTH:i:sP)%";s:6:"author";a:2:{s:5:"@type";s:6:"Person";s:4:"name";s:5:"Jared";}s:11:"description";s:144:"Learn how to navigate the Linux filesystem using the Linux terminal. This guide will get you on the fast track to leveling up your Linux skills.";s:8:"metadata";a:3:{s:5:"title";s:7:"Article";s:9:"isPrimary";b:1;s:4:"type";s:8:"template";}}'
rank_math_analytic_object_id:
  - 36
categories:
  - Linux
series:
  - Linux Terminal Basics
tags:
  - debian
  - linux terminal

---
In this guide, we will be taking a look at how to navigate the file system with the Linux terminal. I would say this is probably the next most important task for beginners to perform, as it will be quite useful. To begin, let&#8217;s open up a terminal. If you don&#8217;t know how to open a terminal, I would recommend referring to [part one][1] of this series and walk through that guide first.

![Linux Terminal Basics](https://learn.yorkcs.com/wp-content/uploads/2019/07/terminal.png)

By default, your terminal is running &#8220;inside&#8221; the logged-in user&#8217;s home directory. You can find where you are relative to the rest of the file system via the _pwd_ command.

![](https://learn.yorkcs.com/wp-content/uploads/2019/07/terminal-pwd.png)

We can also see the files and folders in the directory we&#8217;re currently in. To see the list of these files and folders, we can utilize the _ls_ command.

![](https://learn.yorkcs.com/wp-content/uploads/2019/07/terminal-ls.png)

If we want to move around the file system, the _cd_ command is what we&#8217;re looking for. Let&#8217;s say we want to move into the _Documents_ folder, which we can access since we&#8217;re in our home directory. We can move into the Documents folder by running the command:

_cd Documents_

![](https://learn.yorkcs.com/wp-content/uploads/2019/07/terminal-cd-documents.png)

You may notice that our current path (highlighted by the blue text on our current line) changed from _~_ to _~/Documents_. This means that we are now in the Documents folder! Fantastic.

But what if we want to go back to our previous directory? Well, there&#8217;s a couple ways we can do this. If we want to move up a level (move back to the parent directory), we can type:

_cd ../_

If we run this, you will notice our path changed from _~/Documents_ back to _~_. Let&#8217;s go back to our Documents folder. It&#8217;s your turn to try it!

Once you&#8217;re back in the Documents folder, how can we move back to our home directory without moving up a level? The answer is we can enter an absolute path. Let&#8217;s try typing the following, just be sure to change _jared_ to the username of your user account.

_cd /home/jared_

Once you have, you should now see the blue tilde again.

Perhaps you might want a shortcut to navigate to your home directory. There is one. Let&#8217;s go back into our documents folder with _cd Documents_. Remember the tilde? Let&#8217;s try entering that into our _cd_ command!

_cd ~_

If we run this, you should now be back in your home directory! Pretty cool, huh?

Let&#8217;s put these commands into practice by visiting the root directory. This directory is the root of all the files in the Linux file system. We know that we&#8217;re in our home directory currently, as represented by the tilde. Something neat that we can do is chain multiple _../_ strings together to move up more than one level. In our case, we will need to move up two levels to get to the root directory. This is because, if we only move up one level, we will only be in our _/home_ directory (not to be confused with our user account&#8217;s home directory as represented by the name of your user account.) Let&#8217;s try running the following command:

_cd ../../_

![](https://learn.yorkcs.com/wp-content/uploads/2019/07/terminal-cd-to-root.png)

Try running the command we covered earlier to list the files and folders, you should see the following list of files and directories:

![](https://learn.yorkcs.com/wp-content/uploads/2019/07/terminal-root-ls.png)

With that, you now know how to move within your file system using the terminal! You&#8217;re on the way to becoming a pro at using the terminal!

If you found this guide valuable, please consider sharing it on your social media platform of choice. Also, if you would like to receive news of new tutorials and courses we publish, be sure to fill out the [form][2] to sign up for our newsletter.

 [1]: https://learn.yorkcs.com/2019/07/02/linux-terminal-basics-updating-and-upgrading/
 [2]: https://yorkcs.activehosted.com/f/1