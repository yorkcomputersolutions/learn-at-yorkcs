---
title: A Nibble of HTML
author: Jared
type: post
date: 2019-06-22T15:53:00+00:00
url: /2019/06/22/a-nibble-of-html/
featured_image: /wp-content/uploads/2019/06/HTML5_Logo_512.png
rank_math_internal_links_processed:
  - 1
rank_math_seo_score:
  - 81
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
  - html
rank_math_schema_Article:
  - 'a:6:{s:5:"@type";s:11:"BlogPosting";s:8:"headline";s:11:"%seo_title%";s:13:"datePublished";s:20:"%date(Y-m-dTH:i:sP)%";s:12:"dateModified";s:24:"%modified(Y-m-dTH:i:sP)%";s:6:"author";a:2:{s:5:"@type";s:6:"Person";s:4:"name";s:5:"Jared";}s:8:"metadata";a:3:{s:5:"title";s:7:"Article";s:9:"isPrimary";b:1;s:4:"type";s:8:"template";}}'
rank_math_analytic_object_id:
  - 40
categories:
  - Website Design
tags:
  - beginner
  - html
  - html5
  - nibble
  - website design
  - webdesign
  - webpage

---
 

Hello! This guide is meant to be a tiny introduction to the markup language, HTML. HTML stands for Hypertext Markup Language. This is the language the defines the structure of the websites you visit.

Before we begin writing our own HTML page, create a folder wherever you wish to store the web page. Feel free to name it anything you like. Next, create a file inside that folder and name it _index.html_. This will serve as the main file for our site. This page we&#8217;re making won&#8217;t be accessible via the internet, but you can access it from your computer for the purposes of getting your hands dirty.

Take a second and open our _index.html_ file with a text/code editor of your choice. Anything will work, even a program such as Notepad or Text Edit. Inside our _index.html_ file, we need a way to tell the browser that this is supposed to be interpreted as an HTML document. Easy enough! We just have to add the following:

{{<highlight html>}}
<!DOCTYPE html>
<html>

</html>
{{</highlight>}}

If we take a look at our _index.html_ file in the browser, we will see a blank screen.<figure class="wp-block-image size-large">

<img src="https://learn.yorkcs.com/wp-content/uploads/2019/12/nibble_html_step1-1024x634.png" alt="" class="wp-image-12165" /> </figure> 

Before we continue, it&#8217;s important to point out that HTML is primarily comprised of what&#8217;s known as _tags_. A tag is simply a way that we can reference an HTML _element_. Elements define an object on our page. Some examples of elements include headings, paragraphs, images, headers, footers, etc. In the code above, we have added an opening _<html>_ tag and a closing tag. We can add tags in between to define children of our _<html>_ element. This works for all other tags as well.

Next, we need a way to specify some metadata for our web page. This is pretty trivial as well, just add a set of _<head>_ tags between the _<html>_ tags. It&#8217;s good practice to indent child elements. This makes our markup easier to read. Our document should now look like the following:

{{<highlight html>}}
<!DOCTYPE html>
<html>
    <head>
        
    </head>
</html>
{{</highlight>}}

You may notice when you look at the tabs in your browser, you see the titles for various websites that are in the tabs.<figure class="wp-block-image size-large">

<img src="https://learn.yorkcs.com/wp-content/uploads/2019/12/firefox_tabs-1024x65.png" alt="" class="wp-image-12167" /> </figure> 

We can define a title for our page via the _<title>_ element. We can add this between the _<head>_ tags:

{{<highlight html>}}
<title>My Website</title>
{{</highlight>}}

<figure class="wp-block-image size-large">

<img loading="lazy" width="490" height="205" src="https://learn.yorkcs.com/wp-content/uploads/2019/12/nibble_html_step2.png" alt="" class="wp-image-12168" /> <figcaption>Now we have our renamed tab!</figcaption></figure> 

In order to add content to be displayed on our web page, we will need to add a pair of _<body>_ tags. Add an opening and closing tag after the closing tag of the _<head>_ element. We should now have the following:

{{<highlight html>}}
<!DOCTYPE html>
<html>
    <head>
        <title>My Website</title>
    </head>

    <body>
        
    </body>
</html>
{{</highlight>}}

Let&#8217;s try adding a heading to our page! Between the _<body>_ tags, add the following line:

{{<highlight html>}}
<h1>Hello World!</h1>
{{</highlight>}}

<figure class="wp-block-image size-large">

<img src="https://learn.yorkcs.com/wp-content/uploads/2019/12/nibble_html_step3-1024x616.png" alt="" class="wp-image-12169" /> </figure> 

The _<h1>_ tag is the largest sized heading as specified in the specification. There are also smaller tags such as _<h2>_, _<h3>_, _<h4>_&#8230; all the way up to _<h6>_. Generally it&#8217;s good practice to only have one _<h1>_ heading per page. Under the line above, we can add some text. Please feel free to type anything you like. I&#8217;m just going to add some lorem ipsum filler text, which you can use for your own projects and can find [here][1]. We can add this text via the _<p>_ paragraph element.

{{<highlight html>}}
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vestibulum eu scelerisque enim. Mauris maximus tempus leo, a rutrum mi dignissim nec. Nunc nec quam elementum libero rhoncus rutrum. Donec pulvinar enim id massa condimentum sollicitudin. Aenean nibh risus, luctus sed turpis id, bibendum interdum turpis. Fusce molestie lorem vitae dui hendrerit, ut lacinia ex aliquet. Lorem ipsum dolor sit amet, consectetur adipiscing elit.
</p>
{{</highlight>}}

<figure class="wp-block-image size-large">

<img src="https://learn.yorkcs.com/wp-content/uploads/2019/12/nibble_html_step4-1024x671.png" alt="" class="wp-image-12170" /> </figure> 

You will also find it useful to add lists to your pages at some point. There are two tags that allow us to add lists: _<ul>_ and _<ol>_. The _<ul>_ elements represents an unordered list. Pretty much, this means that by default, the list will have a bullet point next to each item. Let&#8217;s try adding one:

{{<highlight html>}}
<ul>
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
    <li>Item 4</li>
</ul>
{{</highlight>}}

<figure class="wp-block-image size-large">

<img src="https://learn.yorkcs.com/wp-content/uploads/2019/12/nibble_html_step5-1024x663.png" alt="" class="wp-image-12171" /> </figure> 

The other type of list is the ordered list, defined by the _<ol>_ tag. By default, these types of lists will add a number next to each item in sequence. Let&#8217;s try making one!

{{<highlight html>}}
<ol>
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
    <li>Item 4</li>
</ol>
{{</highlight>}}

<figure class="wp-block-image size-large">

<img src="https://learn.yorkcs.com/wp-content/uploads/2019/12/nibble_html_step6-1-1024x665.png" alt="" class="wp-image-12176" /> </figure> 

The way each item is labeled in both lists can be changed via CSS.

The last element I&#8217;ll cover in this bite-sized guide is the anchor tag. The anchor tag allows you to add links to your page. Anchor tags can be specified via the _<a>_ tag. Let&#8217;s try adding one. After our ordered list, add the following line:

{{<highlight html>}}
<a>Click Me!</a>
{{</highlight>}}

<figure class="wp-block-image size-large">

<img src="https://learn.yorkcs.com/wp-content/uploads/2019/12/nibble_html_step7-1024x697.png" alt="" class="wp-image-12177" /> </figure> 

Now, by default this link won&#8217;t go anywhere because we haven&#8217;t specified the destination. We can add a destination by appending what&#8217;s known as an _attribute_ in HTML. Attributes are pretty much key value pairs that we can add to the opening tag of our _<a>_ tag. Let&#8217;s add a destination to our anchor tag via the _href_ attribute.

{{<highlight html>}}
<a href="https://learn.yorkcs.com">Click Me!</a>
{{</highlight>}}

If we open our _index.html_ file in the browser, we should now see something similar to the following:<figure class="wp-block-image size-large">

<img src="https://learn.yorkcs.com/wp-content/uploads/2019/12/nibble_html_step8-1024x690.png" alt="" class="wp-image-12178" /> </figure> 

That about wraps up this nibble of HTML. Hopefully this guide has provided some understanding of the basics of HTML and how you can get started with it right away. If you would like to learn more about HTML, check out our in-depth beginners course available in our [shop][2]!

If you found this guide helpful, and would like to receive news about future tutorials and courses we release, please fill out the [form][3]. Sharing this article on any social media platform is also super appreciated. Thanks for reading!

 [1]: https://lipsum.com/
 [2]: https://learn.yorkcs.com/product/html-beginner-blocks/
 [3]: https://yorkcs.activehosted.com/f/1