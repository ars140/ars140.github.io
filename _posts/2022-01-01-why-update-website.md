---
layout: post
title: Why did I need a 2.0 version of my website?
author: Alex
tags:
- website-1
- website-2
---

Why did I change my website to Jekyll from Python/Django?

When I made the [1.0 version](/projects/website-1.html) of my website, my goal
was to stand up a website and get some hands-on experience with web development
(a far different world than embedded software development). I learned a lot
about HTML and CSS through Django and the development of my original website,
but the original site had some limitations. The database backend in Django is
incredibly powerful, but far more than my limited needs required. I also didn't
like writing posts in the browser. A Markdown preview plugin greatly enhanced
the experience, but still lacked version history. The 1.0 version of my website
largely went dormant after a few months.

My goal with this new site is to start writing more. I dove back into my website
and realized that some simplification could help me, and that everything my site
did previously could largely be recreated with a static site generator. After
evaluating some options, I went with Jekyll. The new site is intentionally
simpler then the old site, and with simplicity comes a lot of benefits:

- Posts are written in plaintext and stored in git
- Version history easily accessible as git repo
- Can be hosted on GitHub Pages for free

I also did some updates on the look of my site, including a dark theme to the
site. Hopefully this gets me writing more!
