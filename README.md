# Moon Jekyll Theme [![Donate](https://img.shields.io/badge/paypal-donate-blue.svg)](https://www.paypal.me/taylantatli/0usd)  
  
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

## Getting Started

To learn how to install and use this theme check out the [Setup Guide](https://taylantatli.github.io/Moon/moon-theme/) for more information.

## Github page setup
- Check the local server dependency in `Gemfile`

- [Github dependency](https://pages.github.com/versions/)
- [Setup local server](https://docs.github.com/en/enterprise/2.14/user/articles/setting-up-your-github-pages-site-locally-with-jekyll)

### [Install Jekyll on Ubuntu](https://jekyllrb.com/docs/installation/ubuntu/#install-dependencies)
- Install Ruby and other prerequisites:
```shell
sudo apt-get install ruby ruby-dev build-essential zlib1g-dev # or ruby-full
```
- Avoid installing Ruby as the root user. Instead, set up a gem installation
directory for your user account. The following commands will add environment
variables to your `~/.bashrc` file to configure the gem installation path:
```
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```
Finally, install Jekyll and Bundler:
```
cd 'lhoangan.github.io'
gem install jekyll bundler
```

### Install bundle

```
bundle install
```

### Update bundler
- After changing the packages' version in `Gemfile`, run
```
bundle update install
```

### Run server
```
bundler exec jekyll server
```





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
