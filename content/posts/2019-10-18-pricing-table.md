---
title: Pricing Table
author: Jared
type: post
date: 2019-10-19T02:15:32+00:00
url: /2019/10/18/pricing-table/
featured_image: /wp-content/uploads/2019/10/pricing-table.png
rank_math_primary_category:
  - 120
rank_math_description:
  - In this guide, we will be building a basic, but modern pricing table. Pricing tables are very useful for conveying subscription plans, etc. to your users.
rank_math_focus_keyword:
  - pricing table
rank_math_robots:
  - 'a:1:{i:0;s:5:"index";}'
rank_math_internal_links_processed:
  - 1
rank_math_analytic_object_id:
  - 8
categories:
  - Website Design
tags:
  - frontend
  - pricing table
  - website design
  - web development

---
## Introduction

In this guide, we will be building a basic pricing table. Pricing tables are commonly used for conveying the prices and features of subscription plans. Clean looking product tables are a great way to help your users subscribe to your services.

## Getting Started

To start, let&#8217;s create a folder and a file inside named _index.html_. Feel free to create the folder anywhere you wish, we won&#8217;t be needing a web server for this.

Open up your _index.html_ file, and add the following HTML boilerplate code:

{{<highlight html>}}
<!DOCTYPE html>
<html>
    <head>
         <meta charset="utf-8">
         <title>Pricing Table Example</title>
         
         <link href="https://fonts.googleapis.com/css?family=Raleway|Rubik&display=swap" rel="stylesheet">
         <style>
             
             html, body {
                 margin: 0;
                 padding: 0;
             }

             body {
                 background: #f1f1f1;
             }

             .wrapper {
                 width: 100%;
                 max-width: 960px;
                 margin: 0 auto;
             }

         </style>
    </head>

    <body>
        <div class="wrapper">

        </div>
    </body>
</html>
{{</highlight>}}

Navigating to our newly created _index.html_ file in the browser, we should see:

![](https://learn.yorkcs.com/wp-content/uploads/2019/10/pricing-table-step-1-4.png "Pretty empty, huh? We'll spruce it up in a sec.")

If you&#8217;re not sure what&#8217;s going on with the boilerplate code, I would recommend you check out my [HTML Beginner Blocks][1] course and [CSS Beginner Blocks][2] course. So far, we wrote out the basic code for our HTML file. All we&#8217;re doing is setting the character set, title, and setting up some basic style rules between our _<style>_ tags.<span style="text-decoration: underline;"></span>

## Flexbox Parent

Many times when there is a pricing table on a website, there are a few plans to choose from. We will be using flexbox, part of CSS, to display the boxes of our pricing table. Flexbox is very flexible and allows us to align items how we like. The first thing we need to add to our wrapper is a _<div>_ element with a class named _pricing-table-flex_. Add the following inside your wrapper _<div>_:

{{<highlight html>}}
<div class="pricing-table-flex">

</div>
{{</highlight>}}

Next, we will be defining some style rules to specify that we want our _<div>_ element to use flexbox. Add the following under our _.wrapper_ style rule between the _<head>_ tags.

{{<highlight css>}}
.pricing-table-flex {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: space-between;
}
{{</highlight>}}

## Flexbox Children

Then, we will need to define _<div>_ elements for each of the plans we will add to our pricing table. Inside the div with class _pricing-table-flex_, add the following divs:

{{<highlight html>}}
<div class="pricing-plan">

</div>

<div class="pricing-plan">

</div>

<div class="pricing-plan">

</div>
{{</highlight>}}

We will want to make each of our plan boxes white. In addition, we only want our boxes to take up a maximum width of 30% of the parent _<div>_. After the _.pricing-table-flex_ rule, add:

{{<highlight css>}}
.pricing-plan {
    background: #ffffff;
    width: 100%;
    max-width: 30%;
}
{{</highlight>}}

Inside each of these plan divs we will need to add a div to apply padding to our boxes. Additionally, we will need to also add an unordered list, and finally a button to each of our boxes. Add this code to each of the divs we added above:

## Adding Padding

{{<highlight html>}}
<div class="pricing-plan-padding">

</div>

<ul class="pricing-plan-features">

</ul>

<div class="pricing-plan-padding">

</div>
{{</highlight>}}

We will step through the code that will go inside each of these elements, one at a time. First, inside the first div with class, _pricing-plan-padding_, add the following code:

## Adding Plan Information

{{<highlight css>}}
<h2 class="pricing-plan-heading">Basic</h2>
<p class="pricing-plan-price">$5/mo</p>
<p class="pricing-plan-info">Learn more about this plan.</p>
{{</highlight>}}

By default HTML is rendered from top to bottom. This is why we define a heading with the name of our plan first. Then, we add the price of our plan. After that we add a small description for our plan. Make sure you added the above code to each of the boxes we&#8217;ve created. I named my payment plans: Basic, Pro, and Platinum. Then I assigned prices to each. So far we should be seeing:

![](https://learn.yorkcs.com/wp-content/uploads/2019/10/pricing-table-step-2-1.png)

Let&#8217;s add style rules for the _<h2>_ element and both paragraph elements. Starting with the heading, add the following rule to our styles:

{{<highlight css>}}
.pricing-plan-heading {
    font-family: "Rubik", sans-serif;
    font-size: 2em;
}
{{</highlight>}}

![](https://learn.yorkcs.com/wp-content/uploads/2019/10/pricing-table-step-3-1.png)

Next, we will want to define the font, as well as adjust the font size of the price of each plan.

{{<highlight css>}}
.pricing-plan-price {
    font-family: "Rubik", sans-serif;
    font-size: 1.5em;
}
{{</highlight>}}

![](https://learn.yorkcs.com/wp-content/uploads/2019/10/pricing-table-step-4.png)

For the summary of each plan, we can add a style affecting the class, _.pricing-plan-info_.

{{<highlight css>}}
.pricing-plan-info {
    font-family: "Raleway", sans-serif;
}
{{</highlight>}}

![](https://learn.yorkcs.com/wp-content/uploads/2019/10/pricing-table-step-5.png)

## Feature List

For each plan, we will also want to include a small list of features. This is where the unordered lists we&#8217;ve added come into play. Add this block of HTML inside each _<ul>_ element:

{{<highlight html>}}
<li>Plan feature #1</li>
<li>Plan feature #2</li>
<li>Plan feature #3</li>
<li>Plan feature #4</li>
<li>Plan feature #5</li>
{{</highlight>}}

Now we will need to add styles for the elements we added above. After our _.pricing-plan_ style rule, add the following CSS to set the padding for each of our box plans.

{{<highlight html>}}
.pricing-plan-padding {
    padding: 32px;
    text-align: center;
}
{{</highlight>}}

At this point, we should see something like this.

![](https://learn.yorkcs.com/wp-content/uploads/2019/10/pricing-table-step-6.png)

For the feature list of each box, we can add the following to our style rules:

{{<highlight css>}}
.pricing-plan-features {
    margin: 0;
    padding: 0;
    list-style-type: none;
    font-family: "Rubik", sans-serif;
}

.pricing-plan-features li {
    padding: 8px 16px 8px 16px;
}

.pricing-plan-features li:nth-child(2n) {
    background: #edf4fc;
}
{{</highlight>}}

In the above code block, first we are defining some styles for the _<ul>_ element representing our feature list. By default, unordered lists display bullet points next to each item. We can remove that via the _list-style-type: none;_ line. We also set the font we wish to use with our feature list. In the second style rule, we are setting the padding of the feature list. The line we wrote includes the shorthand property for defining the padding in each direction for the element. For example, to represent the padding we added above, you could write:

{{<highlight css>}}
padding-top: 8px;
padding-right: 16px;
padding-bottom: 8px;
padding-left: 16px;
{{</highlight>}}

But we can add a line that trivially handles these values for us without adding directions. The arguments we are providing the _padding_ style is as follows:

  * The first argument represents _padding-top_.
  * The second argument represents _padding-right_.
  * The third argument represents _padding-bottom_.
  * The fourth argument represents _padding-left_.

We can also shade every other item of our feature list. We accomplished this by appending _:nth-child(2n)_ to the end of our _.pricing-plan-features li_ rule. That&#8217;s where we used the _background_ property to define a background color.

![](https://learn.yorkcs.com/wp-content/uploads/2019/10/pricing-table-step-7.png)

## Adding Call-to-Action Button

Next, we will add the button to each of our plan boxes. Inside the last div with class _.pricing-plan-padding_ in each box, add:

{{<highlight html>}}
<a class="btn-plan" href="#">Choose Plan</a>
{{</highlight>}}

Perfect! We now have our &#8220;Choose Plan&#8221; buttons, now we just need to make them look fantastic.

Under our last style rule, add the following:

{{<highlight css>}}
.btn-plan {
    color: #ffffff;
    background: #3B70B3;
    padding: 12px 16px 12px 16px;
    text-decoration: none;
    font-family: "Rubik", sans-serif;
}
{{</highlight>}}

![](https://learn.yorkcs.com/wp-content/uploads/2019/10/pricing-table-step-9.png)

There we have it! It looks great on desktops and laptops, but what about mobile devices?

## Mobile Optimization

Let&#8217;s take a look at what we have with the Reponsive Design Mode of Firefox.

![](https://learn.yorkcs.com/wp-content/uploads/2019/10/pricing-table-mobile-unoptimized.png)

Oof! It doesn&#8217;t look great, does it? We can fix this up on mobile devices with the use of CSS media queries! Media queries are the bread and butter of mobile optimization on the web. This is the last CSS we have to add between our _<style>_ tags:

{{<highlight css>}}
@media screen and (max-width: 640px) {
    .pricing-table-flex {
        flex-direction: column;
    }

    .pricing-plan {
        max-width: 90%;
        margin: 0 auto;
        margin-bottom: 32px;
    }
}
{{</highlight>}}

Media queries allow us to define styles that are applied when a condition is true. Above, we are applying some styles only to the screen (not to be printed, etc.), and activate when the screen size is less than 640 pixels.

If we take a look at our page again with Responsive Design Mode or Chrome Web Tools, we should see something similar to this. Congratulations, you build a pricing table and made it mobile optimized!

![](https://learn.yorkcs.com/wp-content/uploads/2019/10/pricing-table-mobile-optimized.gif)

Hopefully this guide has been helpful for you. The HTML file for this tutorial can be downloaded [here][3]. You may be interested in taking a look at our other [website design tutorials][4]. To receive news regarding new tutorials and courses we release, be sure to fill out the [form][5]. If you found this tutorial valuable, sharing it on your favorite social media platform would be highly appreciated.

 [1]: https://learn.yorkcs.com/product/html-beginner-blocks/
 [2]: https://learn.yorkcs.com/product/css-beginner-blocks/
 [3]: https://learn.yorkcs.com/wp-content/uploads/2019/10/PricingTable.zip
 [4]: https://learn.yorkcs.com/category/tutorials/web-design/
 [5]: https://learn.yorkcs.com/newsletter