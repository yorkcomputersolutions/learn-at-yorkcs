---
title: Simple Dropdown
author: Jared
type: post
date: 2019-06-03T20:21:24+00:00
url: /2019/06/03/simple-dropdown/
featured_image: /wp-content/uploads/2019/06/simpledropdown.png
rank_math_internal_links_processed:
  - 1
rank_math_focus_keyword:
  - dropdown
rank_math_seo_score:
  - 66
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
enclosure:
  - |
    |
        https://learn.yorkcs.com/wp-content/uploads/2019/06/simpledropdown.mp4
        463587
        video/mp4
        
  - |
    |
        https://learn.yorkcs.com/wp-content/uploads/2019/06/simpledropdown-1.mp4
        463587
        video/mp4
        
rank_math_schema_Article:
  - 'a:6:{s:5:"@type";s:11:"BlogPosting";s:8:"headline";s:11:"%seo_title%";s:13:"datePublished";s:20:"%date(Y-m-dTH:i:sP)%";s:12:"dateModified";s:24:"%modified(Y-m-dTH:i:sP)%";s:6:"author";a:2:{s:5:"@type";s:6:"Person";s:4:"name";s:5:"Jared";}s:8:"metadata";a:3:{s:5:"title";s:7:"Article";s:9:"isPrimary";b:1;s:4:"type";s:8:"template";}}'
rank_math_analytic_object_id:
  - 43
categories:
  - Website Design
tags:
  - css
  - webdesign

---
Hello everyone! Let&#8217;s dive right into creating our own very simple dropdown menu (or any container.) We won&#8217;t be doing anything fancy with this, other than what is shown in the following preview:

{{< video src="https://learn.yorkcs.com/wp-content/uploads/2019/06/simpledropdown.mp4" type="video/mp4" preload="auto" >}}

To create this dropdown menu, create an HTML file somewhere and name it however you like. Inside this HTML file, let&#8217;s add some basic code:

{{<highlight html>}}
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title>Simple Dropdown</title>
    </head>

    <body>

    </body>
</html>
{{</highlight>}}

Next, we will need to define the markup for our dropdown menu. In order to toggle the menu, we will use a neat trick that we can perform with checkboxes. We can make a checkbox invisible, and use the label to trigger the dropdown. Since labels allow you to specify the ID of the checkbox you want toggled when you click the label, this will work fantastically. Let&#8217;s add the following two lines between the _<body>_ tags:

{{<highlight html>}}
<input id="input-dropdown" type="checkbox">
        <label for="input-dropdown">Click me!</label>
{{</highlight>}}

The first line adds a checkbox, and the second line is the label which triggers the checkbox when clicked. Next we will need to add the element which will expand and retract when clicked. In our case, this will be a _<ul>_ element (unordered list.)

{{<highlight html>}}
<ul id="dropdown">
            <li>Item 1</li>
            <li>Item 2</li>
            <li>Item 3</li>
            <li>Item 4</li>
            <li>Item 5</li>
        </ul><
{{</highlight>}}

Do note that you can put any element in the _<li>_ tags such as an _<a>_ tag for specifying a link.

Finally, we will need to add the styles to make our dropdown menu work. Between the _<head>_ tags, we will need to add a set of style tags:

{{<highlight html>}}
<style>

        </style>
{{</highlight>}}

Inside these style tags, we will first need to add a style rule to make the checkbox invisible. We can reference the checkbox via a pound sign and the ID we specified in our HTML. Add the following style rule:

{{<highlight css>}}
#input-dropdown {
                display: none;
            }
{{</highlight>}}

Next, we want our content (the dropdown) to be collapsed by default. To accomplish this, we will set the _max-height_ property to __. This allows our content to be any size, while still providing the ability to be collapsed. We will also need to set the property, _overflow_, to _hidden_. This allows us to hide content in our dropdown when the _max-height_ is set to __. Let&#8217;s add the style rule for our dropdown:

{{<highlight css>}}
.dropdown {
                max-height: 0;
                overflow: hidden;
            }
{{</highlight>}}

Last, we need to add one last style rule for expanding our dropdown. To do this, we can simply set _max-height_ to _100%_. We will also utilize the _general sibling combinator_. This selector allows us to select the dropdown following our checkbox and label. You can read more about the general sibling combinator from the [MDN web docs][1]. Let&#8217;s add our last style rule:

{{<highlight css>}}
#input-dropdown:checked ~ #dropdown {
                max-height: 100%;
            }
{{</highlight>}}

If we take a look at our page, we should now see our dropdown!

{{< video src="https://learn.yorkcs.com/wp-content/uploads/2019/06/simpledropdown-1.mp4" type="video/mp4" preload="auto" >}}

Hopefully this tutorial can helps a lot of you out! If it has, consider filling out the form to receive news about future tutorials and courses we publish.

 [1]: https://developer.mozilla.org/en-US/docs/Web/CSS/General_sibling_combinator
