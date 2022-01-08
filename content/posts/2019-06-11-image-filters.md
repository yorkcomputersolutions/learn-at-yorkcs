---
title: Image Filters
author: Jared
type: post
date: 2019-06-11T13:32:20+00:00
url: /2019/06/11/image-filters/
featured_image: /wp-content/uploads/2019/06/tut-filters-featured-large.jpg
rank_math_internal_links_processed:
  - 1
rank_math_focus_keyword:
  - image filters
rank_math_seo_score:
  - 73
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
rank_math_schema_Article:
  - 'a:6:{s:5:"@type";s:11:"BlogPosting";s:8:"headline";s:11:"%seo_title%";s:13:"datePublished";s:20:"%date(Y-m-dTH:i:sP)%";s:12:"dateModified";s:24:"%modified(Y-m-dTH:i:sP)%";s:6:"author";a:2:{s:5:"@type";s:6:"Person";s:4:"name";s:5:"Jared";}s:8:"metadata";a:3:{s:5:"title";s:7:"Article";s:9:"isPrimary";b:1;s:4:"type";s:8:"template";}}'
rank_math_analytic_object_id:
  - 41
categories:
  - Website Design
tags:
  - css
  - css3

---

In this tutorial, we will be taking a look at some of the common image filters that are available with CSS. Note, the syntax used in this tutorial may be outdated in the future. The specification seems to still be a working draft as of June 11, 2019. It is my hope that this guide will help you try out this nifty feature of CSS!

First, let&#8217;s create a folder somewhere and add a new file inside named _index.html_. Open this file with your code/text editor of choice. Lately I&#8217;ve taken a liking to Visual Studio Code, but anything works.

We will also need to find an image that we want to manipulate with our image filters. The image we use can either be downloaded or alternatively, we can use the URL of the image on the web. For the purposes of this tutorial, feel free to grab a URL for an image you like. We will need this URL in a minute.

In your _index.html_ file, add the following to create the basic markup for our web page:

{{<highlight html>}}
<!DOCTYPE html>
<html>
  <head>
    <title>Image Filters</title>

    <style>
      /* Add CSS styles here */

    </style>
  </head>

  <body>

  </body>
</html>
{{</highlight>}}

Between the _<body>_ tags, add the following markup for adding our image:

{{<highlight html>}}
<img id="photo" src="<the URL of the image>">
{{</highlight>}}

Of course, you will need to add the URL of the image between the quotes of the _src_ attribute.

![](https://learn.yorkcs.com/wp-content/uploads/2019/06/tut-filters-default.png)

Next, between the _<style>_ tags in the _<head>_ element, add the following style rule:

{{<highlight css>}}
#photo {
  width: 512px;
  height: auto;
}
{{</highlight>}}

Let&#8217;s start by experimenting with the _blur_ filter. Before I get ahead of myself, I should explain that filters can be utilized via the _filter_ property. Now, to add a blur to our image, we can use this _filter_ property and set it to _blur(5px);_ Add the following line to our style rule:

{{<highlight css>}}
filter: blur(5px);
{{</highlight>}}

We should now see the following result:

![](https://learn.yorkcs.com/wp-content/uploads/2019/06/tut-filters-blur.png)

Another commonly used filter is the _brightness_ filter. You can set a percentage below 100%, for darkening an image, or you can set a value above 100% to brighten a picture. Below, I brighten the photo using the line:

{{<highlight css>}}
filter: brightness(200%);
{{</highlight>}}

![](https://learn.yorkcs.com/wp-content/uploads/2019/06/tut-filters-brightness.png)

What if we wanted to adjust the contrast of an image? This is pretty trivial too! You can change the line with our _filter_ property to the following:

{{<highlight css>}}
filter: constrast(200%);
{{</highlight>}}

![](https://learn.yorkcs.com/wp-content/uploads/2019/06/tut-filters-contrast.png)

Another filter that we can use on our websites is the _saturate_ filter. This filter, well&#8230; simply saturates the image. Pretty nifty! We can change the line with our _filter_ property to the following:

{{<highlight css>}}
filter: saturate(200%);
{{</highlight>}}

![](https://learn.yorkcs.com/wp-content/uploads/2019/06/tut-filters-saturate.png)

You might find the need to color your image with a sepia tone. No problem! We can accomplish this by using the _sepia_ function as follows:

{{<highlight css>}}
filter: sepia(200%);
{{</highlight>}}

![](https://learn.yorkcs.com/wp-content/uploads/2019/06/tut-filters-sepia.png)

Before we wrap up, I want to mention that you can also combine filters like so:

{{<highlight css>}}
filter: brightness(180%) contrast(110%) saturate(160%);
{{</highlight>}}

At we can achieve the following result:

![](https://learn.yorkcs.com/wp-content/uploads/2019/06/tut-filters-combo.png)

With that, you now know a handful of the commonly used CSS filters! These filters can really help spruce up your website, so experiment and try them out. If you found this tutorial useful, and would like to receive news on future tutorials and courses we make, be sure to fill out the [form][1]. Sharing this tutorial is also very helpful and much appreciated.

 [1]: https://forms.gle/6TSpUPGsmkckf2Yd6