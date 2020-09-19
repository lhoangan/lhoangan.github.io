# Moon Jekyll Theme [![Donate](https://img.shields.io/badge/paypal-donate-blue.svg)](https://www.paypal.me/taylantatli/0usd)  
  
## `Sorry guys but there will be no update until I buy a new laptop.`
    
######(If you like this theme or using it, please give a :star: for motivation.)

**[Moon](https://taylantatli.github.io/Moon)** is a minimal, one column jekyll theme.

## Features
* Minimal, you can focus on your content
* Responsive
* Disqus integration
* Syntax highlighting
* Optional post image
* Social icons
* Page for sharing projects
* Optional background image
* Simple navigation menu
* MathJax support

## Preview

![screenshot of Moon](https://cloud.githubusercontent.com/assets/754514/14509720/61c61058-01d6-11e6-93ab-0918515ecd56.png)    
![screenshot of Moon](https://cloud.githubusercontent.com/assets/754514/14509716/61ac6c8e-01d6-11e6-879f-8308883de790.png)

See a [live version of Moon](https://taylantatli.github.io/Moon) hosted on GitHub.

## Getting Started

To learn how to install and use this theme check out the [Setup Guide](https://taylantatli.github.io/Moon/moon-theme/) for more information.

## Writing posts
- Clone a post template (where?) or copy it from the template below
- Set the date as a future date to stop the website from being combined (used for
drafting purpose)
- The post file name is `yyyy-mm-dd-[short_filename].md`
  - Remember to put `.md` or the file won't be combined (also to used for drafting
  purpose)
  - The `short_filename` will be the post domain `localhost:4000/short_filename`
- Create an image folder in `assets/images/posts/` in the form of `yyyy-mm-dd` as
in the post filename. However, the matching process will be using the date field
in the template below to retrieve the correct image folder's name.

```
---
layout: post
title: "Modeling projection"
date: 2020-09-19
excerpt: "About homogeneous coordinate"
thumbnail: /assets/images/posts/2018-07-30/pinhole_camera.png
feature: /assets/images/posts/2018-07-30/camera_obscura.jpg
caption: _photo credit_ Camera Obscura [Vondelpark, Amsterdam](https://www.stefnagel.com/22412066/vondelpark-amsterdam) by Stef Nagel

tags:
- research
- computer vision
- camera model
- intrinsic parameter
- homogeneous coordinate
- projection
comments: true
share: true
---
```
