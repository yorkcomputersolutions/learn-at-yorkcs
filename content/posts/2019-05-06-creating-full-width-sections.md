---
title: Creating Full Width Sections
author: Jared
type: post
date: 2019-05-06T04:32:29+00:00
url: /2019/05/06/creating-full-width-sections/
featured_image: /wp-content/uploads/2019/05/webdesign_section_final.png
rank_math_internal_links_processed:
  - 1
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
enclosure:
  - |
    |
        https://learn.yorkcs.com/wp-content/uploads/2019/05/2019-05-05-21-09-10.flv
        11634809
        video/x-flv
        
rank_math_focus_keyword:
  - section
rank_math_schema_Article:
  - 'a:6:{s:5:"@type";s:11:"BlogPosting";s:8:"headline";s:11:"%seo_title%";s:13:"datePublished";s:20:"%date(Y-m-dTH:i:sP)%";s:12:"dateModified";s:24:"%modified(Y-m-dTH:i:sP)%";s:6:"author";a:2:{s:5:"@type";s:6:"Person";s:4:"name";s:5:"Jared";}s:8:"metadata";a:3:{s:5:"title";s:7:"Article";s:9:"isPrimary";b:1;s:4:"type";s:8:"template";}}'
rank_math_analytic_object_id:
  - 55
categories:
  - Website Design
tags:
  - page design
  - site design
  - website design

---
In this tutorial, you will learn how to create sections on a website than span the width of the screen. The cool thing about it is the margins are maintained. It is recommended you have solid knowledge of HTML and CSS before continuing. We Here is an example of what we should see by the end of this tutorial:

{{< video src="https://learn.yorkcs.com/wp-content/uploads/2019/05/2019-05-05-21-09-10.mp4" type="video/mp4" preload="auto" >}}

Without further ado, let&#8217;s jump into the code! Find a home for this tutorial, and create a folder in that location. This folder will serve as our project&#8217;s directory. In that folder, create two folders: css and images. In addition, create a file named _index.html_ and keep that in the project directory. In the css folder, add a file called _styles.css_. You can also find four images on the internet and put them in the images folder. Once you have done that, open _index.html_ with a text editor or code editor of your choice. 

In the _index.html_ file, we will be defining the basis for our web page such as setting the character set, setting the language, resize the viewport for mobile devices, etc. Add the following to your _index.html_ file:

{{<highlight html>}}
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <meta lang="en-us">
    <meta name="viewport" content="width=device-width, initial-scale=1">

    <title>Full Width Sections Example</title>

    <link href="https://fonts.googleapis.com/css?family=Poppins" rel="stylesheet">
    <link rel="stylesheet" type="text/css" href="css/styles.css">
  </head>

  <body>

  </body>
</html>
{{</highlight>}}

The next step we&#8217;ll do is to add the site wrapper div, which we can add CSS to if we want to affect the entire page with properties. Let&#8217;s add this _<div>_ element to the _<body>_ element:

{{<highlight html>}}
<div class="site-wrapper">

</div>
{{</highlight>}}

Inside our site wrapper, we will need to add another _<div>_ which will contain our sections:

{{<highlight html>}}
<div class="site-sections">

</div>
{{</highlight>}}

For the purposes of this tutorial, we will only be adding two background colors for our sections. However, you can add as many as you wish. Generally, it&#8217;s a good idea to have not more than two or three colors in the layout of your website. In the site sections _<div>_, add the following code to create a section:

{{<highlight html>}}
<div class="wrapper-green">
  <section>
    <div class="section-padding">
      <div class="section-image-wrapper">
        <img class="section-image" src="images/nathan-dumlao-1555015-unsplash.jpg" alt="Service 2">
      </div>
      <div class="section-text-padding">
        <h2>Service 2</h2>
        <p>Ut euismod fermentum neque id vulputate. Curabitur pharetra erat ullamcorper justo malesuada efficitur. Mauris sit amet commodo sem. Praesent id libero at nibh dignissim vehicula. Sed posuere malesuada dui, id ornare dolor tincidunt a. Nullam nisi dolor, varius vel blandit sit amet, bibendum ac sem. </p>
      </div>
    </div>
  </section>
</div>
{{</highlight>}}

If we want the image in the section to be left aligned, we&#8217;ll add the _<div>_ containing the image before the _<div>_ element with the text. We can swap the positions of these two divs if we want the image to be right aligned.

Let&#8217;s try it! Add three more sections like above, alternate the wrapper class between &#8220;wrapper-green&#8221; and &#8220;wrapper-blue&#8221;, and alternate the positions of the image and text divs. Once that&#8217;s done, let&#8217;s head over to our _styles.css_ file and start adding our style rules.

The first thing we want to do in our _styles.css_ file is to add a style rule to make the appearance of our site a bit more consistent across browsers. Let&#8217;s start our file with the following code:

{{<highlight css>}}
html, body {
  margin: 0;
  padding: 0;
}
{{</highlight>}}

Next, we&#8217;ll add style rule for the site wrapper. We will be using the _font-family_ property to set the font of all elements on the page.

{{<highlight css>}}
.site-wrapper {
  font-family: 'Poppins', sans-serif;
}
{{</highlight>}}

Note, you may notice the landing page image on the top of the page in the example video. I won&#8217;t be covering how to create the full screen landing page in this tutorial, but you can find my tutorial on that [here][1].

The next part is to add the style rules for the blue and green wrapper divs. Let&#8217;s add them!

{{<highlight css>}}
.wrapper-blue {
  background: #004cff;
}

.wrapper-green {
  background: #078a1f;
}
{{</highlight>}}

This next part is where it gets interesting. The next rule is where we essentially set the &#8220;margin&#8221; on both sides of the section. Let&#8217;s add another little code block:

{{<highlight css>}}
section {
  margin: 0 auto;
  max-width: 960px;
}
{{</highlight>}}

The next two style rules will affect the _h2_ and _p_ elements within any section padding _<div>_. We will just want to set the color of both of these elements to white, since our backgrounds are dark enough.

{{<highlight css>}}
.section-padding h2 {
  color: white;
}

.section-padding p {
  color: white;
}
{{</highlight>}}

We will also want to add a style rule for _<div>_ elements with the class _section-padding_.

The next class for which we will be adding a style rule, _section-padding_, will utilize CSS flexbox! We want an image and a summary displayed next to each other for each section. CSS flexbox allows us to fit the two _<div>_ elements next to each other.

{{<highlight css>}}
.section-padding {
  display: flex;
  flex-direction: row;
  padding: 32px;
  min-height: 380px;
}
{{</highlight>}}

For each _<div>_ element within the section padding div (the div containing the image, and the div containing a summary), we want the width of it to be 40% of the service padding div. Let&#8217;s add this rule:

{{<highlight css>}}
.section-padding div {
  width: 40%;
}
{{</highlight>}}

We will also want to add a bit of padding for the section summary text:

{{<highlight css>}}
.section-text-padding {
  padding: 64px;
}
{{</highlight>}}

By default, the image for each section will be stuck near the top of that section. It will look much nicer to center align the image vertically. To accomplish this, we will enable flexbox on the _section-image-wrapper_ div. This time, instead of using _flex-direction_, we will be using _align-items_.

{{<highlight css>}}
.section-image-wrapper {
  display: flex;
  align-items: center;
}
{{</highlight>}}

The image for each section should take up 100% of the div that it&#8217;s in (which is 40% of the section padding wrapper _<div>_) 

{{<highlight css>}}
.section-image {
  width: 100%;
  height: auto;
}
{{</highlight>}}

That&#8217;s a wrap to get the sections up and running on desktop platforms. However, mobile devices are an enormous percentage of devices accessing the internet. Because of this, let&#8217;s make this design mobile-friendly via CSS media queries! In the code below, any screen that is less than 640 pixels in width will cause the enclosed style rules to override the style rules defined above. Add the following code to add our media query:

{{<highlight css>}}
@media (max-width: 640px) {
  .section-padding {
    flex-direction: column;
  }

  .section-padding div {
    width: 100%;
  }

  .section-text-padding {
    padding: 0;
  }
}
{{</highlight>}}

With that, this tutorial is complete! If we take a look, we should see a similar result to the example video in the beginning of this tutorial. If you have any questions, comments, or other feedback, I&#8217;d like to hear it! You can [email][2] me, or tweet me [@jaredyork_][3].

You can find the source code for this tutorial on [GitHub][4].

If you would like to receive news on our future tutorials and courses, be sure to fill out the [form][5].

 [1]: https://learn.yorkcs.com/2019/04/23/fullscreen-landing-page/
 [2]: mailto://jared.york@yorkcs.com
 [3]: https://twitter.com/jaredyork_
 [4]: https://github.com/jaredyork/TutWebDesignFullWidthSections
 [5]: https://forms.gle/nuPDcYZsozArSPCk9