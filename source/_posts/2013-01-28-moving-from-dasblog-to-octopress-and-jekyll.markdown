---
layout: post
title: "Moving from dasBlog to Octopress/Jekyll"
date: 2013-01-28 07:39
comments: true
categories: 
---
I've decided to move this blog away from dasBlog and over to another platform, [Jekyll](https://github.com/mojombo/jekyll). Jekyll is a static site generator - you create your posts as markdown files, run a command, and it generates all of the files for your blog as static html files. 

Why move away from something more robust? Well, I'm not convinced it was more robust, and it added a lot of complexity to hosting it. Here's my reasoning:

* dasBlog requires a Windows server. I could host it somewhere pretty cheap, but with as much as I've written on this blog (more on that later), I really can't justify spending money on hosting if I could do it for free.
* Jekyll requires no databases, no write permissions to the server, no logins... It's just a static site. Content is written on my laptop, static files are generated and then pushed to the server.
* Jekyll is the engine behind GitHub Pages. That's pretty cool. And you can host your Jekyll blog on GitHub pages for free.
* I considered other blogging platforms, like WordPress, Movable Type, BlogEngine.Net, etc. They all have a host of great features. But in the end I don't really need them. Minimal Viable Blog.

Another key reason for me personally is it allows me to learn some new technology that I'm unfamiliar with. Getting to look under the covers at the Ruby code driving Jekyll and making modificaitons is a fun learning experience.
<!--more-->
I ended up using [Octopress](http://octopress.org), which sits on top of Jekyll. Octopress lets you quickly and easily get up and running. Simply clone the repo, install a theme and you are up and running.

Thankfully I don't have a lot of posts on my dasBlog, so importing them by hand was almost easier than trying to figure out an automated way to do it. I did find a [post](http://doingthedishes.com/2011/04/14/moving-to-jekyll.html) by Derek Morrison where he shared a ruby script to import BlogML, so it is possible to automate it.

So far so good. I'm enjoying the minimalist approach. I've been working on removing complexity from all areas of my life. Writing blog posts in markdown, generating static files and getting them hosted by GitHub for free all align with my goal of simplification.  