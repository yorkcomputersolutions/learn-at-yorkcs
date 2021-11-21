---
title: Simple Navigation Bar
author: Jared
type: post
date: 2019-04-24T14:30:45+00:00
url: /2019/04/24/simple-navigation-bar/
featured_image: /wp-content/uploads/2019/04/navbar-preview.png
rank_math_internal_links_processed:
  - 1
rank_math_seo_score:
  - 31
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
  - 60
categories:
  - Website Design
tags:
  - css
  - frontend
  - nav
  - navbar
  - website design
  - web dev
  - webdesign

---
In this tutorial we will be creating a simple, modern navigation bar. It&#8217;s nothing fancy, it just works, and it looks modern. I&#8217;m deriving the basis of this tutorial from my [full screen landing page][1] tutorial. It&#8217;s not required, but feel free to clone the repository for that tutorial and that can be the basis for our purposes here. It would be helpful to know HTML and CSS, but it&#8217;s not necessarily required, though highly recommended. If you wish to get up to speed with HTML and CSS, you can find my courses, _HTML Beginner Blocks_, and _CSS Beginner Blocks_ in our [shop][2].

If you did not clone the repository I mentioned above, you can follow the steps below to get started:

Create a folder for your project. Inside that folder, create another folder named _css_. In your project directory, add a new file and name it _index.html_. Finally, in the css folder, create a new file called _styles.css_.

We will start by editing the _index.html_ file. Open that file with any old text editor or code editor. Anything will work, so don&#8217;t be afraid to use Notepad or Text Edit if you have to.

Inside the _index.html_ file, add the following to define our HTML file:

{{<highlight html>}}
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <meta lang="en-us">
        <title>Simple Nav Bar</title>

        <link rel="stylesheet" type="text/css" href="css/styles.css">
    </head>

    <body>
        
    </body>
</html>
{{</highlight>}}

Inside the body element, let&#8217;s the code for our navigation bar:

{{<highlight html>}}
<header class="site-header">
    <nav class="nav-main" role="navigation">
        <ul class="navbar">
            <li><a href="#">Home</a></li>
            <li><a href="#">Products</a></li>
            <li><a href="#">Services</a></li>
            <li><a href="#">About</a></li>
            <li><a href="#">Contact</a></li>
        </ul>
    </nav>
</header>
{{</highlight>}}

If we open _index.html_ in our browser, we should now see:<figure class="wp-block-image">

<img src="https://learn.yorkcs.com/wp-content/uploads/2019/04/webdesign-simple-navbar-1024x576.png" alt="" class="wp-image-1137" /> <figcaption>The links are now displayed, that&#8217;s progress!</figcaption></figure> 

Now in our _styles.css_ file, let&#8217;s add the style rule to help make our HTML document appear somewhat more consistent across browsers:

{{<highlight css>}}
html, body {
  margin: 0;
  padding: 0;
}
{{</highlight>}}

Next, let&#8217;s add a style rule for our main _<nav>_ element:

{{<highlight css>}}
.nav-main {
  position: absolute;
  display: inline-block;
  background: rgba(0, 0, 0, 0.5);
  width: 100%;
  z-index: 10;
}
{{</highlight>}}

The first two properties, _position_, and _display_, will allow the navigation bar to overlay any background wrapper. This isn&#8217;t really required, if you don&#8217;t want to make your navigation bar semi-transparent. We&#8217;re using the shorthand property for specifying a background, which is _background_. You can specify a background image, a background color, etc. via this shorthand property. We also want the background color of the navigation bar to span the width of the screen. Finally, we set the _z-index_ (which pretty much means depth), to a higher number like 10. Higher numbers allow the element to be displayed above others with a lower _z-index_.

Next, let&#8217;s add a style rule for the class _navbar_, which is a _<ul>_ (unordered list) element. Essentially, we don&#8217;t want the unordered list to have a bullet point and extra padding, since we&#8217;re displaying them inline. Add the following code to add this rule:

{{<highlight css>}}
.navbar {
    list-style-type: none;
    margin: 0;
    padding: 0;
}
{{</highlight>}}

We will want the list items (_<li>_) elements of the unordered list to be displayed inline. Let&#8217;s add some more code:

{{<highlight css>}}
.navbar li {
    display: inline;
}
{{</highlight>}}

Finally, we can style the links (_<a>_ elements) themselves, which are within the list items:

{{<highlight css>}}
.navbar a {
    color: white;
    display: inline-block;
    padding: 16px;
    font-family: 'Lato', sans-serif;
    text-decoration: none;
}
{{</highlight>}}

If you have a full screen landing page, you should see something like:<figure class="wp-block-image">

<img src="https://learn.yorkcs.com/wp-content/uploads/2019/04/navbar-preview-1-1024x576.png" alt="" class="wp-image-1149" /> </figure> 

Otherwise, if you followed along from scratch, you should see something like:<figure class="wp-block-image">

<img src="https://learn.yorkcs.com/wp-content/uploads/2019/04/webdesign-navbar-scratch-1024x576.png" alt="" class="wp-image-1151" /> </figure> 

If you see a similar result, fantastic! However, if it didn&#8217;t quite turn out right, please don&#8217;t hesitate to email me at [jared.york@yorkcs.com][3] or tweet me at [@jaredyork_][4].

If you found my tutorial valuable, and would like to receive updates on my future tutorials and courses we write, please fill out the [form][5].

You can also find the full source code for this tutorial on [GitHub][6].

 [1]: https://github.com/jaredyork/TutWebDesignFullscreenLanding
 [2]: https://learn.yorkcs.com/product-category/programming-courses
 [3]: mailto://jared.york@yorkcs.com
 [4]: https://twitter.com/jaredyork_
 [5]: https://forms.gle/uUmYEVrNBKvxBo296
 [6]: https://github.com/jaredyork/TutWebDesignSimpleNavBar