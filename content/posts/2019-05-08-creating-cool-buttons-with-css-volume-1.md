---
title: 'Creating Buttons with CSS: Volume 1'
author: Jared
type: post
date: 2019-05-08T07:00:55+00:00
url: /2019/05/08/creating-cool-buttons-with-css-volume-1/
rank_math_internal_links_processed:
  - 1
rank_math_seo_score:
  - 69
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
rank_math_focus_keyword:
  - buttons with css
rank_math_schema_Article:
  - 'a:6:{s:5:"@type";s:11:"BlogPosting";s:8:"headline";s:11:"%seo_title%";s:13:"datePublished";s:20:"%date(Y-m-dTH:i:sP)%";s:12:"dateModified";s:24:"%modified(Y-m-dTH:i:sP)%";s:6:"author";a:2:{s:5:"@type";s:6:"Person";s:4:"name";s:5:"Jared";}s:8:"metadata";a:3:{s:5:"title";s:7:"Article";s:9:"isPrimary";b:1;s:4:"type";s:8:"template";}}'
rank_math_analytic_object_id:
  - 53
categories:
  - Uncategorized
  - Web Design
tags:
  - web development
  - webdesign
  - webdev
  - website
  - website design
  - website development

---
In this tutorial, you will learn how to create buttons via styling them with CSS. If you don&#8217;t have a solid foundation with HTML and CSS, I would highly recommended checking out our free Beginners Blocks courses in our [store][1]. The buttons below are what I will help you learn how to create:<figure class="wp-block-image">

<img loading="lazy" width="556" height="624" src="https://learn.yorkcs.com/wp-content/uploads/2019/05/buttons_vol1.png" alt="" class="wp-image-1272" /> </figure> 

Let&#8217;s dive right into the code. Create a folder somewhere on your computer and name it whatever you want. This folder will be the home of our project. In that folder, create a file named _index.html_ and create another folder called _css_. In the _css_ folder, add a new file and name it _styles.css_.

Once our folders and files are set up, we can open a text editor or code editor of our choice and open our newly created _index.html_ file. The first thing we need to do is define our basic HTML document:

<pre class="EnlighterJSRAW" data-enlighter-language="html" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">&lt;!DOCTYPE html>
&lt;html>
  &lt;head>
    &lt;meta charset="utf-8">
    &lt;meta lang="en-us">
    &lt;title>Buttons Examples Vol. 1&lt;/title>

    &lt;link rel="stylesheet" type="text/css" href="css/styles.css">
  &lt;/head>

  &lt;body>

  &lt;/body>
&lt;/html></pre>

In the _<body>_ element, we are going to need a bunch of buttons to spice up, so add the following:

<pre class="EnlighterJSRAW" data-enlighter-language="java" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">&lt;div class="wrapper">
  &lt;h2>Buttons Vol. 1&lt;/h2>
  &lt;br />

  &lt;a class="btn-type-1" href="#">Download&lt;/a>
  &lt;br />&lt;br />
  &lt;a class="btn-type-2" href="#">Download&lt;/a>
  &lt;br />&lt;br />
  &lt;a class="btn-type-3" href="#">Download&lt;/a>
  &lt;br />&lt;br />
  &lt;a class="btn-type-4" href="#">Download&lt;/a>
  &lt;br />&lt;br />
  &lt;a class="btn-type-5" href="#">Download&lt;/a>
  &lt;br />&lt;br />
  &lt;a class="btn-type-6" href="#">Download&lt;/a>
&lt;/div></pre>

Let&#8217;s head over to our _styles.css_ file. Since we&#8217;re not going to make an actual website, it&#8217;s fine if we give the wrapper _<div>_ a huge amount of padding. Let&#8217;s add a style rule to add a bunch:

<pre class="EnlighterJSRAW" data-enlighter-language="css" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">.wrapper {
  padding: 64px;
}</pre>

#### The First Button<figure class="wp-block-image">

<img loading="lazy" width="600" height="262" src="https://learn.yorkcs.com/wp-content/uploads/2019/05/webdesign_button_1.png" alt="" class="wp-image-1275" /> </figure> 

Now, we can start adding style rules for our buttons, starting with the first. Let&#8217;s add the first style rule:

<pre class="EnlighterJSRAW" data-enlighter-language="css" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">.btn-type-1 {
  display: inline-block;
  padding: 16px 32px 16px 32px;
  border-radius: 3px;
  font-family: arial, sans-serif;
  font-weight: bold;
  text-decoration: none;
  color: white;
  background: #1E88E5;
}</pre>

By setting the _display_ property to _inline-block_, we can kind of get the &#8220;best of both worlds&#8221;, by being able to manipulate the button with properties that affect _display: block_ elements, as well as still allowing the button to be displayed inline. The next property we&#8217;ve added, _padding_, is the shorthand version for defining padding. The first unit represents the top padding, the second stands for the right padding, the third stands for the bottom padding, and the fourth defines the padding on the left. The next property, _border-radius_, is fairly self explanatory. The border radius just means how rounded do you want the corners of the element. For all of these buttons, we will be using Arial as our font, then default to a default Sans Serif font, if Arial is somehow not installed. This is what the _font-family_ property enables us to do. We can set the text in the button to use a bold font face. To do this, we can utilize the _font-weight_ property. Since all of our buttons are anchor tags, they will appear as normal links until we style them. Because the buttons will display like normal links by default, they will display underlines under them. We don&#8217;t want this for our buttons, so we use the _text-decoration_ property, and set the value to _none_. This will remove the underline from the button. The text color for all of our buttons will be white so it shows up well on the backgrounds. To set the text color, we can utilize the _color_ property. To set the background color of the button, we will use the shorthand _background_ property. When defining colors with CSS, we can either define them with hexadecimal color values, or using the color keywords provided in CSS. We can change the appearance of the button when you move the mouse over it via the following:

<pre class="EnlighterJSRAW" data-enlighter-language="css" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">.btn-type-1:hover {
  background: #1565C0;
}</pre>

We can append the _:hover_ selector to our _.btn-type-1_ selector. This will cause the specified styles to take effect when hovered over.

If we want the button to change appearance when you click/press down it, we can use the _:active_ selector.

<pre class="EnlighterJSRAW" data-enlighter-language="css" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">.btn-type-1:active {
  background: #0D47A1;
}</pre>

#### The Second Button<figure class="wp-block-image">

<img loading="lazy" width="600" height="262" src="https://learn.yorkcs.com/wp-content/uploads/2019/05/webdesign_button_2.png" alt="" class="wp-image-1550" /> </figure> 

The second button will not need a button color, however we will be adding a border. We will also be adding a transition animation between button states. So, if you were to move your mouse over the button, it will transition from the current color to a new color over a period of time. Let&#8217;s add the code!

<pre class="EnlighterJSRAW" data-enlighter-language="css" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">.btn-type-2 {
  display: inline-block;
  padding: 16px 32px 16px 32px;
  font-family: arial, sans-serif;
  font-weight: bold;
  text-decoration: none;
  border: 2px solid #2E7D32;
  border-radius: 32px;
  color: #2E7D32;
  transition: 0.2s ease-in-out;
}</pre>

When the user hovers over the button, we want to change the text color as well as the border color. 

<pre class="EnlighterJSRAW" data-enlighter-language="css" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">.btn-type-2:hover {
  border: 2px solid #555;
  color: #555;
}</pre>

Feel free to add another set of styles for the _:active_ selector.

#### The Third Button<figure class="wp-block-image">

<img loading="lazy" width="600" height="262" src="https://learn.yorkcs.com/wp-content/uploads/2019/05/webdesign_button_3.png" alt="" class="wp-image-1552" /> </figure> 

Now, we will be taking a look at buttons with gradients. Specifically, we will make use of linear gradients. We can combine a border with a linear gradient. Let&#8217;s put this into practice:

<pre class="EnlighterJSRAW" data-enlighter-language="css" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">.btn-type-3 {
  display: inline-block;
  padding: 16px 32px 16px 32px;
  font-family: arial, sans-serif;
  font-weight: bold;
  text-decoration: none;
  border: 2px solid #B71C1C;
  border-radius: 10px;
  color: white;
  background-image: linear-gradient(#EF5350, #E53935);
}</pre>

The first argument for the _linear-gradient_ function is the background color on the top of the button, and the second is the background color displayed on the bottom of the button. We can also change the colors of the gradient via the _:hover_ and _:active_ selectors as well. Let&#8217;s add some style properties for the _:hover_ selector:

<pre class="EnlighterJSRAW" data-enlighter-language="css" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">.btn-type-3:hover {
  background-image: linear-gradient(#F44336, #E53935);
}</pre>

We can provide a different color variation for the _:active_ selector too!

<pre class="EnlighterJSRAW" data-enlighter-language="css" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">.btn-type-3:active {
  background-image: linear-gradient(#E53935, #EF5350);
}</pre>

#### The Fourth Button<figure class="wp-block-image">

<img loading="lazy" width="600" height="262" src="https://learn.yorkcs.com/wp-content/uploads/2019/05/webdesign_button_4.png" alt="" class="wp-image-1559" /> </figure> 

This next button has a more modern look to it, while maintaining a slightly less serious tone. We can add some depth to the bottom of the button by using the _border-bottom_ property.

<pre class="EnlighterJSRAW" data-enlighter-language="css" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">.btn-type-4 {
  display: inline-block;
  padding: 16px 32px 16px 32px;
  font-family: arial, sans-serif;
  font-weight: bold;
  text-decoration: none;
  border-bottom: 4px solid #1B5E20;
  border-radius: 6px;
  color: white;
  background: #388E3C;
}</pre>

Then, we can add a set of properties for the _:hover_ selector:

<pre class="EnlighterJSRAW" data-enlighter-language="css" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">.btn-type-4:hover {
  background: #43A047;
}</pre>

After that, we want to move the button down 4 pixels, but also offset that with a margin of four pixels so the buttons don&#8217;t push other elements down when the user presses the button. All of this will take place using the _:active_ selector:

<pre class="EnlighterJSRAW" data-enlighter-language="css" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">.btn-type-4:active {
  position: relative;
  top: 4px;
  border-bottom: 0;
  margin-bottom: 4px;
  background: #2E7D32;
}</pre>

#### The Fifth Button<figure class="wp-block-image">

<img loading="lazy" width="600" height="262" src="https://learn.yorkcs.com/wp-content/uploads/2019/05/webdesign_button_5.png" alt="" class="wp-image-1563" /> </figure> 

This button is similar to the previous one, however this one has a shadow around the base. This further gives the perception of depth to the button. We can accomplish this via the _box-shadow_ property. Let&#8217;s add the code affecting the class _btn-type-5_:

<pre class="EnlighterJSRAW" data-enlighter-language="css" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">.btn-type-5 {
  display: inline-block;
  padding: 16px 32px 16px 32px;
  font-family: arial, sans-serif;
  font-weight: bold;
  text-decoration: none;
  border-bottom: 8px solid #4A148C;
  border-radius: 6px;
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.85);
  color: white;
  background: #AB47BC;
}</pre>

Let&#8217;s take a look at our use of the _box-shadow_ property. The first unit defines the horizontal offset of the shadow. The second unit represents the vertical offset of the shadow. The third unit represents how far the shadow should spread. Finally, the fourth is the color of the shadow. We can define a semi-transparent color using the _rgba_ function notation. In this case, we want to use a black color with 85% transparency. Next, we can add our usual _:hover_ selector properties:

<pre class="EnlighterJSRAW" data-enlighter-language="css" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">.btn-type-5:hover {
  background: #BA68C8;
}</pre>

Finally, we can add a set of styles for the _:active_ selector. This time, we will decrease the spread of the _box-shadow_ to make it smaller. When we add this, the &#8220;depth&#8221; of the button will appear like it&#8217;s actually pressed down.

<pre class="EnlighterJSRAW" data-enlighter-language="css" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">.btn-type-5:active {
  position: relative;
  top: 8px;
  border-bottom: 0;
  margin-bottom: 8px;
  background: #9C27B0;
  box-shadow: 0px 1px 2px rgba(0, 0, 0, 1);
}</pre>

#### The Sixth Button<figure class="wp-block-image">

<img loading="lazy" width="600" height="262" src="https://learn.yorkcs.com/wp-content/uploads/2019/05/webdesign_button_6.png" alt="" class="wp-image-1568" /> </figure> 

This final button has a glassy look to it. It almost looks like it came from the Windows 7 Aero era. It looks pretty cool and nostalgic! This type of button also looks great with any color. The styles for the default state of this button is quite similar to the gradient buttons above. The main difference is the addition of the _:after_ selector. Let&#8217;s first start by adding the styles for the _.btn-type-6_ selector:

<pre class="EnlighterJSRAW" data-enlighter-language="css" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">.btn-type-6 {
  display: inline-block;
  position: relative;
  padding: 16px 32px 16px 32px;
  font-family: arial, sans-serif;
  font-weight: bold;
  text-decoration: none;
  border-radius: 3px;
  box-shadow: 0px 1px 4px -2px #333;
  text-shadow: 0px -1px #333;
  color: white;
  background: linear-gradient(#E65100, #EF6C00);
}</pre>

We can add the shine effect from the top of the button using this selector:

<pre class="EnlighterJSRAW" data-enlighter-language="css" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">.btn-type-6:after {
  content: '';
  position: absolute;
  top: 2px;
  left: 2px;
  width: calc(100% - 4px);
  height: 50%;
  background: linear-gradient(rgba(255, 255, 255, 0.75), rgba(255, 255, 255, 0.2));
}</pre>

We can finish up by adding the _:hover_ and _:active_ selectors.

<pre class="EnlighterJSRAW" data-enlighter-language="css" data-enlighter-theme="" data-enlighter-highlight="" data-enlighter-linenumbers="" data-enlighter-lineoffset="" data-enlighter-title="" data-enlighter-group="">.btn-type-6:hover {
  background: linear-gradient(#E65100, #EF6C00);
}

.btn-type-6:active {
  background: linear-gradient(#EF6C00, #E65100);
}</pre>

With that, let&#8217;s take a look at the result in our browser. Open the _index.html_ file and we should see the following:<figure class="wp-block-image">

<img loading="lazy" width="556" height="624" src="https://learn.yorkcs.com/wp-content/uploads/2019/05/buttons_vol1.png" alt="" class="wp-image-1272" /> </figure> 

CSS allows developers and designers so many options to create beautiful, sleek websites. We hope this tutorial has been useful for you. If it has, and would like to receive updates on future tutorials and courses we release, be sure to fill out the [form][2]. Sharing this tutorial on social media platforms of your choice would be highly appreciated. We made this easy by adding share buttons to the bottom of each of our posts.

The full source code for this tutorial can also be found on [GitHub][3].

 [1]: https://learn.yorkcs.com/product-category/programming-courses
 [2]: https://forms.gle/zfe1NhaqHAwM7aj86
 [3]: https://github.com/jaredyork/TutWebDesignButtonsVol1