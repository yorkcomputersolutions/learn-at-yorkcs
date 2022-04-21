---
title: "WordPress from Scratch - 10: Designing a Homepage"
date: 2022-01-08T22:07:56+0000
draft: true
categories:
    - WordPress
series:
    - WordPress from Scratch
---


## Introduction
In this part of _WordPress from Scratch_, I will be walking through how to design a homepage from scratch.  The Full Site Editing capabilities of WordPress 5.9 is what will enable us to fully design a homepage, without the need for a page builder.  Full site editing will allow WordPress websites to be much more lightweight which gives a nice bump in speed from many website builders out there.

## Creating a Header
In the previous part of _WordPress from Scratch_, I give an overview of template parts.  To begin building our site, we will start by creating a template part for a custom header.

First, let's begin by opening the Site Editor.  You can either go to _Appearance > Editor_ in the dashboard, or you can click the _Edit Site_ button in the topbar.

Once the editor loads, you should see the following screen:

{{< figure src="./site-editor.png" >}}

Next, click the black WordPress logo button in the top-left corner. 

{{< figure src="./editor-wordpress-logo-button.png" >}}

After clicking this button a sidebar will appear on the left.  Click the _Template Parts_ tab.  You will then see a list of template parts.

{{< figure src="./editor-template-parts-default.png" >}}

We could edit the default header, but this is _WordPress from Scratch_, plus I generally prefer to just create a _new_ template part rather than modifying the original template parts.

Let's start by clicking on the blue _Add New_ button in the top-right corner of the screen.

{{< figure src="./editor-template-parts-add-new-button.png" >}}

Name the template part _Custom Header_ (or anything at all, really), select the _Header_ area, then click the blue _Create_ button in the bottom left corner of the modal.

{{< figure src="./editor-create-template-part-custom-header.png" >}}

After creating the template part, you will see a blank slate in the editor that we can build on.  

{{< figure src="./editor-new-template-part-custom-header.png" >}}

Many websites you visit probably have a logo on the left side of the header.  We can utilize the _Columns_ block to allow us to put a block (an image for our logo) on the left side, and put the navigation links on the right side.

Start by clicking the blue _+_ button at the top-left corner of the screen.

{{< figure src="./blue-add-block-button.png" >}}

After clicking this button, the block inserter will open.  Type _column_ or _columns_ in the search box, you should see the _Columns_ block show up.

{{< figure class="width-50perc" src="./editor-search-block-column.png" >}}

Click the _Columns_ block once it appears.

{{< figure class="width-100perc" src="./editor-columns-select-variation.png" >}}

The columns block will prompt you to choose how you want the columns divided to start.  The really nice thing about the editor is that you can give columns a specific width if any of the variations aren't what you're looking for.

Generally though, logos will take up a relatively small part of the header.  Since we want the logo to be smaller and placed on the left side, the _30 / 70_ variation will best fit our needs.

{{< figure src="./editor-columns-variation-30-70.png" >}}

Once you select this variation, you will see two spots where you can add blocks.

{{< figure src="./editor-columns-variation-selected.png" >}}

If you have an image to use as a logo, you can add an image block next.  Otherwise, let's just add the name of our site here.

One really great thing about searching for blocks is that most blocks have aliases.  For example, you don't have to type _paragraph_ to add a paragraph block.  You can search _text_ for example, and the paragraph block will still appear.  This feature should be helpful for people coming from different page builders.

{{< figure class="width-75perc" src="./editor-header-column-left-add-site-name.png" >}}

This is where we will write the name of our site.  For a lack of a better name, I just wrote, "Jared's Company Site."

{{< figure class="width-100perc" src="./header-with-site-name.png" >}}

Before we continue, it would be nice to be able to take a look at our header so far on our site.  We will first have to replace the default header provided by Twenty-Twenty Two with our custom header.

Head over to the Templates screen.


## In Conclusion
In the next part of _WordPress from Scratch_, we will be building an about page.


