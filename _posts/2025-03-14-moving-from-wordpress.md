---
layout: post
title: Moving From WordPress
description: I've done it before and it looks like I'm doing it again. It just may be the right time to move my [personal blog](htpp://www.bobrockefeller.com) from WordPress to a static site for simplicity, portablity, and performance.
image:
category: Web Development
tags:
date: 2025-03-14 19:28 -0400
---

I've done it before and it looks like I'm doing it again. It just may be the right time to move my [personal blog](htpp://www.bobrockefeller.com) from WordPress to a static site for simplicity, portablity, and performance.

<!--more-->

My objectives for this move are:

- Portability -- you can export a WordPress site into various formats but all of them take a lot of work to make functional in a new system.
- Performance -- WordPress on my shared hosting site just wasn't very fast.
- Security -- a static site doesn't have near as many vectors for hacking as a WordPress site.
- Convenience -- I can write articles in Markdown nearly anywhere and not have to be logged into WordPress

With that in mind, I knew I wanted to use a static site generator and write in relatively simple Markdown. So I needed to pick the right static site generator for this project. My experiments, so far, have been with Jekyll and I like it. But the fact is that Jekyll is a mature system with few updates and many themes that are no longer maintained or are being maintained for backward compatibility with the old GitHub pages workflow.

This lack of updates to the system and the themes lead me to consider a few other popular static site generators.

Next.js
: Written in JavaScript and using React templates, this one is very popular. But it's more of an application framework that can create static sites.

Hugo
: Written in Go and using Go templates, Hugo is coming on like gangbusters. One of its claims to fame is the speed with which it can generate a site.

Nuxt
: Another JavaScript application framework, but using Vue templates.

Gatsby
: And another JavaScript application framework using React templates!

Astro
: More JavaScript and many possible template languages.

So I'm trying out Hugo. I don't want the complexity of an application framework for a static site blog, and learning Go might be interesting. It should take care of my performance, security, and convenience objectives. The portability part will take a bit of work, and discipline, on my part.

Markdown is an inherently portable document format. But plain old Markdown doesn't offer more than the very basics in formatting. Not even Definition Lists, Fenced Code Blocks, Tables, or Footnotes. These features, and others, are implemented in the many Markdown alternatives such as kramdown (Ruby), CommonMark (PHP), markdown-it (JavaScript), and GoldMark (Go).

And that's the problem. The Markdown alternatives don't all agree on syntax and features. Floating an image to the right with a caption requires everything from shortcodes, to plug-ins, to clever syntax. None of that is very portable.

The good news for making image display more interesting is that all the Markdown alternatives respect plain HTML. That let's me copy and paste a block of code and just edit the image path.

```HTML
<figure style="float: right; width: 50%; margin: 1em 0em 1em 1em">
  <img src="/images/image,jpg" alt="Alternate Text" >
  <figcaption>Caption</figcaption>
</figure>
```

Making the caption look nice just takes a little CSS in the theme.

```CSS
figcaption {
  text-align: center;
  font-size: 0.85rem;
}
```

Being aware of portability includes what goes in the YAML front matter. For example, some static site generators use an excerpt maker in the text (`<!--more-->`) and others expect the excerpt to be in the `description:` in the front matter. So articles I'm writing now use both; the `<!--more-->` will just be ignored by generators not using it.

So far Hugo is working out pretty well. The learning curve is a little bit steep for me, not knowing GO, and Hugo's documentation doesn't help -- it's broken into so many little pieces that finding what you want is better done with a web search. But most of the available themes are well maintained and several of them are very nice. Right now I'm working with Roadster which is a fork of Mainroad because that author no longer maintains it. Hugo has a lot of updates and some of them break themes, so maintenance is important.

Hugo is indeed very fast generating my site. Jekyll was plenty fast enough, but Hugo is almost instant. Its development server is very good at seeing file changes and updating the browser withc makes tweaking things so much easier.
