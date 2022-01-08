---
title: Feature Boxes
author: Jared
type: post
date: 2019-04-25T04:23:39+00:00
url: /2019/04/25/feature-boxes/
featured_image: /wp-content/uploads/2019/04/webdesign-featurebox-preview.png
rank_math_internal_links_processed:
  - 1
rank_math_seo_score:
  - 27
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
  - 59
categories:
  - Website Design
tags:
  - design
  - feature
  - html
  - website design
  - web dev
  - webdesign

---
In this tutorial we will show you how to create feature boxes with HTML and CSS. Feature boxes are common on many websites and help summarize services or products a business offers, etc.

The final result will look like the following:
![](https://learn.yorkcs.com/wp-content/uploads/2019/04/webdesign-featurebox-preview.png)

Before jumping into the code, it will be useful for you to download the _images_ folder containing the icons shown above for our feature boxes. You can download the ZIP file with the _images_ folder and associated icons [here][1].

The first thing we&#8217;re going to do is create a directory for our project. Create a folder somewhere and name it whatever you want. Inside that folder another folder called _css_. Extract the ZIP we just downloaded, and move the _images_ folder into our project directory. Inside the css folder, add a new file named _styles.css_. Then, in our main project folder, create a new file named _index.html_.

Next, open our _index.html_ file with any text editor or code editor and add the following to define the basis of our HTML document:

{{<highlight css>}}
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <meta lang="en-us">
    <meta name="viewport" content="width=device-width, initial-scale=1">

    <title>Feature Boxes Example</title>

    <link href="https://fonts.googleapis.com/css?family=Lato|Open+Sans" rel="stylesheet">
    <link rel="stylesheet" type="text/css" href="css/styles.css">
  </head>

  <body>
    
  </body>
</html>
{{</highlight>}}

Basically, we just defined some boilerplate code we need, as well as load in the fonts we&#8217;ll use. We also linked in our _styles.css_ file. 

The next thing we&#8217;ll do is define the markup for our feature boxes. If you haven&#8217;t learned about HTML or CSS yet, you can find my Beginner Blocks courses for each language in our [shop][2]. If you&#8217;re comfortable with each language, let&#8217;s proceed with creating our wrapper _<div>_ element. Add the following to the _<body>_ element of our HTML document.

{{<highlight html>}}
<div class="wrapper">

</div>
{{</highlight>}}

Inside this new div, we will want to add another wrapper which we&#8217;ll use as a parent container for holding our feature boxes. This new _<div>_ will use the _feature-wrapper_ class. Add this code to the wrapper div:

{{<highlight html>}}
<div class="feature-wrapper">

</div>
{{</highlight>}}

For the purposes of this tutorial, we will be adding four feature boxes. Type the following code within the _feature-wrapper_ div:

{{<highlight html>}}
<div class="feature-box">
  <object class="feature-icon" type="image/svg+xml" data="images/icon_book.svg">
    Your browser doesn't support SVG.
  </object>
  <h4>Feature 1</h4>
  <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nam quis dolor ipsum.</p>
</div>

<div class="feature-box">
  <object class="feature-icon" type="image/svg+xml" data="images/icon_rain.svg">
    Your browser doesn't support SVG.
  </object>
  <h4>Feature 2</h4>
  <p>Integer tempus vulputate quam, et ultricies odio. Quisque suscipit consequat est.</p>
</div>

<div class="feature-box">
  <object class="feature-icon" type="image/svg+xml" data="images/icon_computer.svg">
    Your browser doesn't support SVG.
  </object>
  <h4>Feature 3</h4>
  <p>Duis semper pulvinar auctor. In vehicula magna sagittis, elementum diam eu, porttitor lorem.</p>
</div>

<div class="feature-box">
  <object class="feature-icon" type="image/svg+xml" data="images/icon_laptop.svg">
    Your browser doesn't support SVG.
  </object>
  <h4>Feature 4</h4>
  <p>Sed mauris nunc, semper eu auctor vel, consequat vitae ligula. Integer aliquet sodales enim, ut ornare lacus.</p>
</div><
{{</highlight>}}

Essentially, we&#8217;re creating four _<div>_ elements we&#8217;ll be using to represent our feature boxes. The icons I have added for this tutorial are SVG files, so I added them via the _<object>_ elements. If an SVG file couldn&#8217;t be loaded, the text &#8220;Your browser doesn&#8217;t support SVG.&#8221; will be displayed.

The next step is to add the style rules needed for the feature boxes. Let&#8217;s head over to the _styles.css_ file. In that file, we&#8217;ll want to start by adding a little code to help make our page appear a bit more consistent across browsers:

{{<highlight css>}}
html, body {
  margin: 0;
  padding: 0;
}
{{</highlight>}}

Now, we&#8217;ll also add a background color to our site. This will help make our wrapper element stand out, and many modern websites feature a light background with a white wrapper:

{{<highlight css>}}
body {
  background: #e9e9e9;
}
{{</highlight>}}

Next, we&#8217;ll add the style rule for our main site wrapper:

{{<highlight css>}}
.wrapper {
  background: white;
  margin: 0 auto;
  width: 100%;
  max-width: 960px;
}
{{</highlight>}}

In the code above, we make the wrapper white, we center it horizontally, and we instruct the browser to stretch it to a maximum width of 960 pixels.

Now we&#8217;ll add the style rule for the feature box wrapper I described earlier. We will be specifying we want to use CSS flexbox to display the feature boxes (which are children of the _feature-wrapper_ div.)

{{<highlight css>}}
.feature-wrapper {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  align-items: middle;
  flex-wrap: wrap;
}
{{</highlight>}}

Let&#8217;s now add the code to style feature boxes themselves. We will want them to stretch to 45% the width of the feature box wrapper, but stay less than 320 pixels in width. We will also set the padding around each feature box, and center align the heading and summary text.

{{<highlight css>}}
.feature-box {
  width: 45%;
  max-width: 320px;
  padding: 48px 32px 48px 32px;
  text-align: center;
}
{{</highlight>}}

The next two style rules we&#8217;ll add affect the heading and summary text. We&#8217;ll utilize the font _Lato_ for each feature box heading, and _Open Sans_ for the summary in each box. If either (or both) Google Web Fonts fail to load, for example, if the user was offline, then it will fallback to the device&#8217;s default sans-serif font.

{{<highlight css>}}
.feature-box h4 {
  font-family: 'Lato', sans-serif;
}

.feature-box p {
  font-family: 'Open Sans', sans-serif;
}
{{</highlight>}}

The last style rule we need to add is for the feature icons. We want the height of each icon to be constrained to 128 pixels, which will keep the headings and summaries aligned on each row of feature boxes.

{{<highlight css>}}
.feature-icon {
  max-width: 128px;
  height: 100%;
  max-height: 128px;
}
{{</highlight>}}

If we open our _index.html_ file with the browser, we should see our final result!

![](https://learn.yorkcs.com/wp-content/uploads/2019/04/webdesign-featurebox-preview-1.png)

With that, this concludes the tutorial! If you have found it useful, please fill out the [form][3] if you would like to receive news about future tutorials and courses we release. If you have any questions, comments, or just general feedback, don&#8217;t hesitate to contact me via [email][4], our contact form, or tweet at me @[jaredyork_][5]. It would also be much appreciated if you took a moment and shared this tutorial on your social media platform of choice with our new buttons below if you liked it.

You can also find the full source code for this tutorial on [GitHub][6].

 [1]: http://www.mediafire.com/file/0rxpg05au4471w4/TutWebDesignFeatureBoxesIcons.zip
 [2]: https://learn.yorkcs.com/product-category/programming-courses
 [3]: https://forms.gle/Xtyz2gxyEbvnfHFw6
 [4]: mailto://jared.york@yorkcs.com
 [5]: https://twitter.com/jaredyork_
 [6]: https://github.com/jaredyork/TutWebDesignFeatureBoxes