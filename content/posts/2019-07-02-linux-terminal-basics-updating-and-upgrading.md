---
title: Linux Terminal Basics – Updating and Upgrading
author: Jared
type: post
date: 2019-07-02T18:08:44+00:00
url: /2019/07/02/linux-terminal-basics-updating-and-upgrading/
featured_image: /wp-content/uploads/2019/07/series-thumb-update-upgrade-square.png
rank_math_internal_links_processed:
  - 1
rank_math_seo_score:
  - 62
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
  - linux terminal
rank_math_schema_Article:
  - 'a:6:{s:5:"@type";s:11:"BlogPosting";s:8:"headline";s:11:"%seo_title%";s:13:"datePublished";s:20:"%date(Y-m-dTH:i:sP)%";s:12:"dateModified";s:24:"%modified(Y-m-dTH:i:sP)%";s:6:"author";a:2:{s:5:"@type";s:6:"Person";s:4:"name";s:5:"Jared";}s:8:"metadata";a:3:{s:5:"title";s:7:"Article";s:9:"isPrimary";b:1;s:4:"type";s:8:"template";}}'
rank_math_analytic_object_id:
  - 37
categories:
  - Linux
series:
  - Linux Terminal Basics

---
This is the beginning of a series where I cover the basics of using the terminal in Debian/Ubuntu based distributions. Chances are, if you&#8217;re using another distribution that isn&#8217;t based of Debian (or Ubuntu), you already know these basic commands. The goal of this series of tutorials is to start you on your journey of utilizing the command line in Linux. Without further ado, let&#8217;s start by learning how to update and upgrade your computer via the terminal.

If you&#8217;re using Ubuntu, you can open an instance of the terminal by pressing the super key (also known as the Windows key associated with that other nasty operating system, haha.) Next, you should see a search box at the top of your screen where you can search for an application. Start typing in &#8220;terminal.&#8221; As you type, you should see the terminal application appear like so:<figure class="wp-block-image">

<img loading="lazy" width="982" height="644" src="https://learn.yorkcs.com/wp-content/uploads/2019/07/ubuntu-search-terminal.jpg" alt="" class="wp-image-3025" /> </figure> 

Once the icon appears, feel free to click on it or simply press enter.<figure class="wp-block-image">

<img loading="lazy" width="982" height="644" src="https://learn.yorkcs.com/wp-content/uploads/2019/07/terminal.jpg" alt="" class="wp-image-3026" /> <figcaption>The only part of Windows I like is the Bliss wallpaper from Windows XP, don&#8217;t judge me.</figcaption></figure> 

When I update and/or upgrade my system, a run a series of commands that perform the following steps:

  * Update the list of available packages
  * Upgrade installed packages to the latest version
  * Update the Linux kernel
  * Auto-remove old, unnecessary packages
  * Safely clear the cache of package files used when updating

Having to run these five commands may be a little daunting, but don&#8217;t worry. Let&#8217;s try these one by one.

#### Update List of Available Packages

Now that your terminal is open, type in:

<pre class="EnlighterJSRAW" data-enlighter-language="generic" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">sudo apt-get update</pre><figure class="wp-block-image">

<img loading="lazy" width="982" height="644" src="https://learn.yorkcs.com/wp-content/uploads/2019/07/terminal-apt-update.jpg" alt="" class="wp-image-3027" /> </figure> 

Now that we have a refreshed list of packages, next we can update our existing packages to the new versions that we&#8217;ve retrieved. We can update our packages by typing:

<pre class="EnlighterJSRAW" data-enlighter-language="generic" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">sudo apt-get upgrade</pre><figure class="wp-block-image">

<img loading="lazy" width="982" height="644" src="https://learn.yorkcs.com/wp-content/uploads/2019/07/terminal-apt-upgrade.jpg" alt="" class="wp-image-3028" /> </figure> 

Occasionally, we will also want to update the Linux kernel. This is actually a very important step to do. Kernel updates provide fixes to loopholes, exploits, better hardware compatibility, increased speed, and other new features. It&#8217;s generally recommended that you use your terminal to upgrade your Linux kernel instead of manually downloading the latest and installing. If you try to install the absolute latest kernel, there&#8217;s a good chance your graphics drivers, and many of your other applications will break. This is why it&#8217;s good to upgrade to the kernel your distribution recommends via the command:

<pre class="EnlighterJSRAW" data-enlighter-language="generic" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">sudo apt-get dist-upgrade</pre><figure class="wp-block-image">

<img loading="lazy" width="982" height="644" src="https://learn.yorkcs.com/wp-content/uploads/2019/07/terminal-apt-dist-upgrade.jpg" alt="" class="wp-image-3029" /> </figure> 

After upgrading our packages, we will want to get rid of packages that are no longer needed by the newest releases of the software we have installed. We can run the following command to do so:

<pre class="EnlighterJSRAW" data-enlighter-language="generic" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">sudo apt-get autoremove</pre><figure class="wp-block-image">

<img loading="lazy" width="982" height="644" src="https://learn.yorkcs.com/wp-content/uploads/2019/07/terminal-apt-autoremove.jpg" alt="" class="wp-image-3032" /> </figure> 

After you&#8217;ve been running the _sudo apt-get update_ command a bunch of times, you might want to clear out the old temporary package files. These files can build up as you install and upgrade packages. We can clean out the old package files with the command:

<pre class="EnlighterJSRAW" data-enlighter-language="generic" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">sudo apt-get clean</pre><figure class="wp-block-image">

<img loading="lazy" width="982" height="644" src="https://learn.yorkcs.com/wp-content/uploads/2019/07/terminal-apt-clean-2.jpg" alt="" class="wp-image-3034" /> </figure> 

Now you know the main commands to update and upgrade your Linux system running a Debian or Ubuntu variant! In the next part of this series, we will take a look at another useful tool that you can use via the terminal. Until then, stay tuned! If you found this guide helpful, please be sure to share it on your social media platform of choice. You can also fill out the form [here][1], to receive news on our upcoming tutorials and courses!

 [1]: https://yorkcs.activehosted.com/f/1