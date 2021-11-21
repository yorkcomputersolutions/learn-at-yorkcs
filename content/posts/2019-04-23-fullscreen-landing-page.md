---
title: Full Screen Landing Page
author: Jared
type: post
date: 2019-04-23T23:30:57+00:00
url: /2019/04/23/fullscreen-landing-page/
featured_image: /wp-content/uploads/2019/04/fullscreen-landing-preview.jpg
rank_math_internal_links_processed:
  - 1
rank_math_seo_score:
  - 29
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
enclosure:
  - |
    |
        https://learn.yorkcs.com/wp-content/uploads/2019/04/full-screen-landing-page.mp4
        17550889
        video/mp4
        
rank_math_schema_Article:
  - 'a:6:{s:5:"@type";s:11:"BlogPosting";s:8:"headline";s:11:"%seo_title%";s:13:"datePublished";s:20:"%date(Y-m-dTH:i:sP)%";s:12:"dateModified";s:24:"%modified(Y-m-dTH:i:sP)%";s:6:"author";a:2:{s:5:"@type";s:6:"Person";s:4:"name";s:5:"Jared";}s:8:"metadata";a:3:{s:5:"title";s:7:"Article";s:9:"isPrimary";b:1;s:4:"type";s:8:"template";}}'
rank_math_analytic_object_id:
  - 61
categories:
  - Website Design
tags:
  - fullscreen
  - html
  - landing page
  - website design
  - webdesign

---
Hello everyone! This will be the start of my web design tutorials. In this little tutorial, we will be creating a full screen landing page.

Here&#8217;s a preview of what we&#8217;ll be making:<figure class="wp-block-video"><video controls src="https://learn.yorkcs.com/wp-content/uploads/2019/04/full-screen-landing-page.mp4"></video></figure> 

To start, let&#8217;s head over to [Unsplash][1] so we can pick out a picture we want. I really like the sunset picture you see in the preview by Samuel Zeller (available [here][2]). When you find the picture you want to use, just click the large green &#8220;Download&#8221; button on the image preview. The image should then download. If you already have a nice big photo in mind that you wish to use, that will work just fine.

Next, create a folder we can base our project in. Inside that folder, create two more folders: _images_, and _css_. Move the image you downloaded into the images folder. Let&#8217;s also add a new file to our project directory and name it _index.js_. Finally, in our _css_ folder, create a new file and name it _styles.css_. Let&#8217;s now start adding to our index.html file. Open our newly created index.html file with your text editor or code editor of choice. If you don&#8217;t have a dedicated code editor, you can even use Notepad or Text Edit, anything will work. Once you opened our HTML file, add the following:

{{<highlight js>}}
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <meta lang="en-us">
    <meta name="viewport" content="width=device-width, initial-scale=1">

    <title>Fullscreen Landing Example</title>

    <link href="https://fonts.googleapis.com/css?family=Lato|Open+Sans" rel="stylesheet"> 
    <link rel="stylesheet" type="text/css" href="css/styles.css">
  </head>

  <body>
    <div class="landing-outer-wrapper">
      <div class="landing-inner-wrapper">
        <div class="landing-centered">
          <h1>My New Website</h1>
          <h4>Hello world!</h4>
        </div>
      </div>
    </div>
  </body>
</html>
{{</highlight>}}

If you don&#8217;t recognize what much of the above code does, I would recommend checking out my _HTML Beginner Blocks_ course available [here][3]. Essentially, we are specifying that our file is an HTML document, we added a _<meta>_ tag for making our website mobile friendly. We also link in the two Google Web Fonts we&#8217;ll be using: Lato, and Open Sans. Those are two modern looking fonts. Then we&#8217;re also linking in our _styles.css_ file. Finally, we add in the HTML elements we need to make our full screen landing page work. Now, we can hop over and add the CSS to our _styles.css_ file.

First, let&#8217;s add a few lines of code to help standardize the appearance of our web page across most browsers:

{{<highlight css>}}
html, body {
  margin: 0;
  padding: 0;
}
{{</highlight>}}

We will be using a specific method for horizontally and vertically aligning the _<div>_ element. Let&#8217;s start by adding the following style to class _landing-outer-wrapper_:

{{<highlight css>}}
.landing-outer-wrapper {
  display: table;
  position: absolute;
  width: 100%;
  height: 100vh;
}
{{</highlight>}}

Basically, we&#8217;re going to make the browser display our outer wrapper similar to a table. Child elements of the outer wrapper (the inner wrapper), will be affected by this. We also want our outer wrapper to stretch across the screen, hence the 100% width, and we want it to be as tall as the user&#8217;s screen, hence the 100vh height. The unit _vh_ is the viewport height, and 1% vh represents 1% of the height of the screen.<figure class="wp-block-image">

<img loading="lazy" width="936" height="768" src="https://learn.yorkcs.com/wp-content/uploads/2019/04/fullscreenlandingpage-notmuchcss.png" alt="" class="wp-image-1113" /> </figure> 

So far, if we open our index.html file in your browser of choice, you will notice the page looks pretty empty. The picture isn&#8217;t appearing in the background yet. No worries! Let&#8217;s add the following within our _.landing-outer-wrapper_ rule, after the _height_ property:

{{<highlight css>}}
background-image: url();
background-size: cover;
background-repeat: no-repeat;
{{</highlight>}}

Now, we haven&#8217;t actually added the URL (path) to our image yet. It&#8217;s important to point out we need to write the path to our image relative to the location of our CSS file. Since the _styles.css_ file is within the _css_ folder we made, we have to make the path go back a directory to the root of our project directory, then refer to the _images_ folder and our image. Obviously, if we wanted to refer to the URL of an image located online, we can simply add the URL inside the two parenthesis. However, since we saved our photo locally in the _images_ directory, we will have provide a relative path. Here is the path I added to the _url_ functional notation:

{{<highlight css>}}
background-image: url(../images/samuel-zeller-19361-unsplash.jpg);
{{</highlight>}}

Notice how I&#8217;ve included &#8220;../&#8221; before the path to the images folder, this allows us to go back a directory. We also added two other properties: _background-size_, and _background-repeat_. We want our background image to cover the div, but we don&#8217;t want it to repeat if the height of the image is shorter than the page when scaled.

Now if we refresh our browser, we should now see our photo fully covering our page.<figure class="wp-block-image">

<img loading="lazy" width="948" height="767" src="https://learn.yorkcs.com/wp-content/uploads/2019/04/fullscreenlanding-bgimg-defined.png" alt="" class="wp-image-1110" /> </figure> 

The next step is to specify we want elements with the class _landing-inner-wrapper_ to be displayed similar to a table cell. In this style rule we will also set the vertical alignment of the inner wrapper to be in the middle. Add the following code to create our style rule:

{{<highlight css>}}
.landing-inner-wrapper {
  display: table-cell;
  vertical-align: middle;
}
{{</highlight>}}

Inside this inner wrapper div we also added a div which contains our two headings and is centered. Let&#8217;s add some more code to our CSS file:

{{<highlight css>}}
.landing-centered {
  margin: 0 auto;
  width: 960px;
  height: 300px;
}
{{</highlight>}}

We have to specify the width and height of the div we&#8217;re centering, in this case a div with the class _landing-centered_. We&#8217;re now finished with the meat and potatoes of centering the _landing-centered_ div.<figure class="wp-block-image">

<img src="https://learn.yorkcs.com/wp-content/uploads/2019/04/fullscreenlanding-centered-div-1024x576.png" alt="" class="wp-image-1120" /> </figure> 

Now we just need to modernize the appearance of our text! Add the following style rules to center align our headings, color them white, and add a slight text shadow:

{{<highlight css>}}
.landing-centered h1, .landing-centered h4 {
  color: white;
  text-align: center;
  text-shadow: 0px 1px 3px rgba(0, 0, 0, 0.3);
}

.landing-centered h1 {
  margin: 0;
  font-family: 'Lato', sans-serif;
  font-size: 6em;
}

.landing-centered h4 {
  font-family: 'Open Sans', sans-serif;
  font-size: 2em;
}
{{</highlight>}}

<figure class="wp-block-image">

<img src="https://learn.yorkcs.com/wp-content/uploads/2019/04/fullscreenlanding-almost-finished-1024x576.png" alt="" class="wp-image-1121" /> </figure> 

The last thing we&#8217;ll probably want to do is make our page mobile responsive. To do this, we will utilize CSS media queries. Pretty much, as the width of the window decreases below 960 pixels, we will want to decrease the font size and make adjustments to the width for some of our divs. Add the following code for our media query used for changing styles if the screen width is below 960 pixels:

{{<highlight css>}}
@media (max-width: 960px) {
  .landing-centered {
    width: 100%;
    height: 160px;
  }

  .landing-centered h1 {
    font-size: 4.5em;
  }
}
{{</highlight>}}

Finally, we will want to add one last media query if the screen width is less than 640 pixels. Basically we&#8217;re performing the same instructions as the code above, but we&#8217;re making the font smaller, and also readjust the width of the _landing-centered_ div. Add this block of code to the bottom of our _styles.css_ file:

{{<highlight css>}}
@media (max-width: 640px) {
  .landing-centered {
    width: 100%;
    height: 160px;
  }

  .landing-centered h1 {
    font-size: 3em;
  }

  .landing-centered h4 {
    font-size: 1.25em;
  }
}
{{</highlight>}}

Our final result should look like our first preview! And with that, this concludes my first web design tutorial. If you have any questions, comments, or feedback, I&#8217;d love to hear it. You can either fill out the [contact form][4], email me at [jared.york@yorkcs.com][5], or tweet at me [@jaredyork_][6].

If you found this tutorial valuable, and would like to receive future updates on new tutorials and courses we release, please fill out the [form][7]. Using the share buttons at the bottom of this post to share this tutorial on the platform of your choice would be highly appreciated!

The full source code for this tutorial can be found on my [GitHub][8].

 [1]: https://unsplash.com/
 [2]: https://unsplash.com/photos/UI45Xkj_5aU
 [3]: https://learn.yorkcs.com/product/html-beginner-blocks/
 [4]: https://learn.yorkcs.com/contact
 [5]: mailto://jared.york@yorkcs.com
 [6]: https://twitter.com/jaredyork_
 [7]: https://forms.gle/tG6BqRYYYBr1a2A29
 [8]: https://github.com/jaredyork/TutWebDesignFullscreenLanding