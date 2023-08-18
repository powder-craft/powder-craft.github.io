---
layout: post
title: Personal Blog with GitHub Pages and Jekyll
description: Create a Blog with GitHub Pages and Jekyll, what I did
image: assets/images/create-a-blog-with-github-pages-jekill.png
image-caption: Dall-e 2 image, generated after requesting a seaotter with a ruby earring, oil painting
---

## Introduction
If you have the ability, you should have a blog for yourself. Maybe you are not going to
use it everyday, but you will sure learn something new in doing it.<br>

There are several different ways to create a blog, some are better (in many ways) than other,
but in the end the result is the same, so you should choose a way of deploying it
that you find interesting and doable for what you have (especially money 💶).<br>

I choose to use GitHub Pages with Jekyll, because it is free, already connected to a repository,
so the deployment is easier, and I thougth Jekyll was not so difficult and I found it interesting.

## Setting up GitHub pages
This step was so easy and very well documented on [the GitHub pages page](https://pages.github.com).
The only step I was not sure about was when I created the ✨special✨ repository and I typed in my username,
it recognized already that I wanted to use GitHub Pages without the need to type in the whole address
(as indicated in the link).<br>

Still, I typed in the full address, because I like guides and I like to follow them because I can very easily
get lost in the process.

## Setting up Jekyll
I do not like all the work behind a good looking, responsibe web page. I do not like arguing with CSS because I am not
able to center divs. So I gave Jekyll a go, since it is so well integrated with GitHub Pages.<br>

It is indeed so easy to just write a markdown file and it automagically gets transformed in a beatiful (and responsive) web page.<br>

On the other end, the installation of ruby was a time-consuming operation. You need ruby (and then Jekyll) on your machine if you want to see what your site will look like, not for other purposes. I am using WSL 2 for this project
and this added a whole new level of difficulty. Here are the main guides that I followed:

- [GitHub pages docs](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/about-github-pages-and-jekyll)
- [Jekyll docs for Windows](https://jekyllrb.com/docs/installation/windows/)

So, the first error that I made was considering WSL 2 as "pure" Linux, so I went straight to the Linux installation
page and my plan was incredibly <s>cunning</s> stupid.<br>

I installed ruby, since Jekyll is written in ruby, but I had an error that went like this:

    Loading the rubygems/defaults/operating_system.rb file caused an error. This file is owned by your OS.

The text is taken from one of the [stackoverflow question](https://stackoverflow.com/questions/72532160/unable-to-update-ruby-file-owned-by-os) I used to have some clues about the error.<br>

Obviously I could not resolve the error in any way that was indicated by helping users in various forums.
So I gave up and opened the Windows installation docs in Jekyll's site, and what did I find 👀 oh my god 👀,
the "Installation via Bash on Windows 10".<br>

I followed the directions, but had so many troubles when running

    gem update

in particular I had errors like troubles with version of gems. I was crying hard.<br>

I found out that the version they suggest to use from the Jekyll documentation is outdated.
You should use the [last ruby version that brightbox has to offer](https://www.brightbox.com/docs/ruby/ubuntu/#:~:text=Brightbox%20have%20been%20providing%20optimised,3%2C%20and%201.8.), that is, as I am writing, the 2.7.<br>

But beware if you have different version of ruby or you had one version of ruby installed and you think you
uninstalled it "completely".
I had the 2.5 version (as indicated as I am writing), and I tried to removed it with

    sudo apt-get remove ruby2.5

because I wanted to install the 2.7 version, but that was not enough. If you want to completely unistall ruby, you have to purge every version you have

    sudo apt-get purge ruby

and you have to remove manually ALL the libraries and gems. You can find them with

    find ruby

After you removed everything (and reverted any change to the ./bashrc file, if you did something to it), you can redo a clean installation of ruby. After changing the version, everything
was running smoothly. An afternoon was lost, but a blog was created.<br>

I tried changing the theme of my GitHub page with one that was supported natively,
following [this guide](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/adding-a-theme-to-your-github-pages-site-using-jekyll) but I wasn't able to do that, all I had were white pages.
I still do not know how to change the theme to a supported one.<br>

I came across to [this site](https://jekyllthemes.io/free) and find [this theme](https://jekyllthemes.io/theme/forty-jekyll-theme) in the first page and I thought it looked stunning. I got to the [repository](https://github.com/andrewbanchich/forty-jekyll-theme) and found out that I had to take the files and use it on my repository.<br>

After taking all the essential files and learning the structure of a Jekyll site, it ended up like [the repository of the site](https://github.com/powder-craft/powder-craft.github.io).

## Structure of Jekyll project

I will very briefly summarize what I understood about the Jekyll project file structure.<br>

There are pages and posts. Pages are in the root directory and are standalone, instead posts are in the _posts directory and have some requirements on them.
This requirements are:

- the name of the post file needs to be in the format **YEAR-MONTH-DAY-title.markdown**
- they need to be in the _posts directory
- the have to start with the front matter

They can have tags or categories, that are similar, but categories have a strong relationship with the post path.<br>

The front matter is between three dashes, over and under, and it has the YAML syntax. You can only add ASCII chars in there. You have to define the layout of the page (that has to be defined in the _layout directory) and the title.
You can also define other variables that you can call in the corrisponding HTML file.<br>

The _config.yml file has to be correctly defined and if you follow the GitHub guide, without subdirectories, then you do not need to change the URL and baseurl variable.
In this file you can also define other variables and some variables are required by the theme that I decided to use, like:

    tiles-source: posts

This was a very intresting start of a project I hope I will use forever.<br>

Thank you for reading, bye for now 🚀<br>

Gaia