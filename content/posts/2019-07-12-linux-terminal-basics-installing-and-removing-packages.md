---
title: Linux Terminal Basics – Installing and Removing Packages
author: Jared
type: post
date: 2019-07-12T17:13:45+00:00
url: /2019/07/12/linux-terminal-basics-installing-and-removing-packages/
featured_image: /wp-content/uploads/2019/07/series-thumb-installing-removing-packages.png
rank_math_internal_links_processed:
  - 1
rank_math_focus_keyword:
  - terminal
rank_math_seo_score:
  - 65
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
rank_math_description:
  - Learn how to install and remove packages from the Linux terminal! This is an important step to mastering the terminal on your Linux system.
rank_math_schema_Article:
  - 'a:7:{s:5:"@type";s:11:"BlogPosting";s:8:"headline";s:11:"%seo_title%";s:13:"datePublished";s:20:"%date(Y-m-dTH:i:sP)%";s:12:"dateModified";s:24:"%modified(Y-m-dTH:i:sP)%";s:6:"author";a:2:{s:5:"@type";s:6:"Person";s:4:"name";s:5:"Jared";}s:11:"description";s:139:"Learn how to install and remove packages from the Linux terminal! This is an important step to mastering the terminal on your Linux system.";s:8:"metadata";a:3:{s:5:"title";s:7:"Article";s:9:"isPrimary";b:1;s:4:"type";s:8:"template";}}'
rank_math_analytic_object_id:
  - 35
categories:
  - Linux
series:
  - Linux Terminal Basics
tags:
  - install
  - linux terminal
  - terminal

---
Hey there! In this guide, we will be taking a look at how to install and remove packages via the terminal!

To begin, let&#8217;s start by opening the terminal. I have covered how to open the terminal in the last couple parts of this series. If you haven&#8217;t read them, I would recommend checking out [part one][1] and [two][2].

![](https://learn.yorkcs.com/wp-content/uploads/2019/07/terminal-1.png)

Once you&#8217;ve opened your terminal, let&#8217;s try installing an application. Applications are made up of what are known as _packages_ in Linux. Let&#8217;s just say we wanted to install VLC player. Not a problem! Type the following:

_sudo apt-get install vlc_

![](https://learn.yorkcs.com/wp-content/uploads/2019/07/terminal-install-vlc.png)

We can&#8217;t install packages by default as a normal user. This is why we need to run the command as a _super user_. We can specify this via adding _sudo_ before the command. Press &#8216;enter&#8217;, then type your password when it prompts you. If you don&#8217;t see your password as you type, that&#8217;s normal, don&#8217;t worry about it. Once you press &#8216;enter&#8217; again, there will be another prompt asking if you want to install the list of packages it found.

![](https://learn.yorkcs.com/wp-content/uploads/2019/07/terminal-instasll-vlc-yesno.png)

If we press &#8216;y&#8217;, then hit &#8216;enter&#8217;, we should see the installation proceed.

![](https://learn.yorkcs.com/wp-content/uploads/2019/07/terminal-instasll-vlc-installed.png)

See the cursor? Fantastic! Now you can install and remove packages from the terminal! You are on your way to becoming a pro at this.

If you found this guide useful, consider [signing up for our newsletter][3]! Also, sharing this article on a social media platform of your choice would be much appreciated as well.

 [1]: https://learn.yorkcs.com/2019/07/02/linux-terminal-basics-updating-and-upgrading/
 [2]: https://learn.yorkcs.com/2019/07/03/linux-terminal-basics-navigating-the-file-system/
 [3]: https://yorkcs.activehosted.com/f/1