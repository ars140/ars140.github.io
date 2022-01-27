---
layout: post
title: Migrating to Website Version 2.0
author: Alex
tags:
- website-2
---

Here's a quick overview of how I migrated from my [version 1.0
website](/projects/website-1.html) to my new [version 2.0
website](/projects/website-2.html).

I decided to redo my site using the static site generator
[Jekyll](https://jekyllrb.com) from [Django](https://www.djangoproject.com) [for
simplicity](/2021/12/31/why-update-website.html), after which I could update the
design of the site. To get familiar with Jekyll, I followed the
[tutorial](https://jekyllrb.com/docs/step-by-step/01-setup/) on the Jekyll
website to get the solution set up and to go through the basics.

## Back to Basics

In order to have a solid base on which I could iterate the design of the site, I
decided to first replicate the basic structure of my site in Jekyll. I replaced
the old Django templates with updated Liquid templates. Things such as the
[Projects](/projects) page, which I use to aggregate all of the posts with a
certain project tag into a group, were easy to implement using Jekyll's
[Collections](https://jekyllrb.com/docs/collections/) feature. Using the CSS
from my old website as-is, I was able to quickly get the functionality of the
old site implemented using Jekyll.

## GitHub Pages Setup

Once the basic functionality of the new site matched the old site, I created a
new [git repo](https://github.com/ars140/ars140.github.io) pushed it to GitHub.
Then, I configured the repo to publish the site as a GitHub Pages site so that I
could ensure the site built and deployed properly.

- In the Settings > Pages for the personal website's GitHub repo, I set the
  visibility of the site to Public
- GitHub Pages supports Jekyll, so the site will automatically rebuild and
  deploy on commit using GitHub Actions as long as the site is Public
- GitHub Pages deploys each site at a location determined by the project
  repo's name (*\<user\>.github.io/\<GitHub project name\>/*). Because I
  intend this to be a user page and not a project page (and therefore not
  have the extra *\<project name\>/* at the end of the link), I made sure the
  name of my personal website's GitHub repo was "\<user\>.github.io"
- Once the site was deployed, I could preview the site and make sure the
  basic functionality worked as I expected

## Design Refresh

Next, I started the process of updating the site design. I prefer Dark Mode or
dark themes where possible, so I decided on a dark theme for my website. I used
a [hex color generator](https://coolors.co/generate) to help generate the color
palette of the site. I spent some time iterating on the design and modifying the
CSS to change the post and project layouts. I'm pleased with how it looks for
quickly updating the site over a weekend.

## Hooking Up a Custom Domain

Last, I hooked up my custom domains to the new site. I use [Google
Domains](https://domains.google) to manage my domains. GitHub Pages has
[detailed
instructions](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site)
on how to configure your site using a custom domain. After setting that up, and
waiting a couple of minutes for the change to propagate, my site was ready to go!
