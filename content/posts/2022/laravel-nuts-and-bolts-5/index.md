---
title: "Laravel Nuts and Bolts - 5: Application Styling"
date: 2022-01-015T22:07:56+0000
draft: true
categories:
    - Laravel
series:
    - Laravel Nuts and Bolts
---

## An Introduction
Up until this point in _Laravel Nuts and Bolts_, we have been focusing on the back-end of our application.  In this tutorial, I will be covering how to make our application look better.  You may have noticed that it looks quite bland and boring up until this point.

I wanted to split the back-end portion of this series from the front-end.  Reason being, is so those who just want to learn how to program using Laravel can do so unencumbered by anything related to the front-end.

In this tutorial, I will be explaining how to style our application with plain CSS, as well as the four most popular CSS frameworks (according to this [dev.to article by ThemeSelection](https://dev.to/), written in December, 2020).

Please feel free to click the framework listed below that interests you to jump to it.
### Table of Contents
1. [Plain CSS](#plain-css)
2. [Tailwind CSS](#tailwind-css)
3. [Bootstrap](#bootstrap)
4. [Materialize CSS](#materialize-css)

## Plain CSS
Laravel doesn't automatically compile and copy resources such as CSS files by default.  You will either have to create asset directories and assets in the `public` directory manually, or create a pipeline.

Laravel does however provide an easy way to build an asset pipeline, using _Laravel Mix_.  _Mix_ makes it simple to define Webpack build steps.

_Mix_ is already defined in your project's `package.json` file when you create a fresh Laravel project.  All you will need to do is install the NPM modules.  Type the following command to install your project's defined NPM modules, including Mix:

> _sail npm install_

During development you can use this command to run all Mix tasks:

> _sail npm run dev_

For building for a production environment, you can use this command to run all Mix tasks and minify the output of your resources:

> _sail npm run prod_

If you were to use a CSS framework hosted at a _content delivery network_ (CDN) such as _Tailwind CSS_, you will not need to run these commands as CDN files are not stored within your project.

All fresh Laravel projects will contain an `app.css` file located in the `resources/css` directory.  Open this file.  This is where our app's styles will go.

While writing CSS styles, you can use the `sail npm run watch` command to watch for changes to our stylesheets.  What does "watching" mean?  Watching for changes means that our resource files will be automatically packaged when we change anything in our resource files.  When we change a resource file and save it, we can reload the page in our browser without typing `sail npm run dev` each time.  It's a beautiful thing.

It's worth noting, though, that Webpack might not detect changes to your files in some local development environments.  If you find this command doesn't work, try running this command instead:

> _npm run watch-poll_



## Tailwind CSS

## Bootstrap

## Materialize CSS

## In Conclusion
In part six of this series, the final part, we won't be writing any code.  Rather, I will just be providing some ideas of features and changes you can make to the application we created.  You can read the final part [here](https://learn.yorkcs.com/2022/laravel-nuts-and-bolts-6/).
