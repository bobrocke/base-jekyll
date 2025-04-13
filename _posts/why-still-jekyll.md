---
layout: post
title: Why Still Jekyll?
date: 2025-04-05
lastmod:
summary:
description:
draft: true
categories: []
tags: []
---

With the tremendous variety of static site generators available, why am I still running this blog on Jekyll? Next.js can build whole applications, Hugo is lightening fast at generating a site, and Eleventy is super flexible. Jekyll is still being updated and its simplicity suits blogging.

<!--more-->

I've had a go with Jekyll, Hugo, and Eleventy (with a brief stop over with Zola and Next.js). Hugo seemed the best fix, despite its oddities, and I got my blog running it on Netlify. It was good.

But as I've gone back to add and tweak, I keep getting slowed down the complicated way Hugo [automatically finds layouts] and by my lack of familiarity with the Go Template Language. That template language has its own quirks. One of them is that a comment in a layout gets executed! If you just want to include a comment in the output file you need syntax like this: `{{ "<!-- baseof.html. -->" | safeHTML }}`. Another is the unusual way to use a conditional:`{{ if ne $title .Name }}`. That means 'if $title is not equal to .Name'.

Jekyll just seems simpler.

Documentation is good and it's been around so long that there are years worth of guides, posts, and Stack Overflow answers to go to for help.

I do worry that something in Jekyll's dependencies will break and that there won't be a fix due to age and potential lack of maintenance.

Jekyll: `{{ post.date | date_to_string: "ordinal", "US" }}`

Eleventy: `{{ modifiedDate | postDate }}`

```js
import { DateTime } from "luxon";
const TIME_ZONE = "America/New_York";

eleventyConfig.addFilter("postDate", (dateObj) => {
  let thisDateTime = DateTime.fromJSDate(dateObj, { zone: "utc" }).setZone(
    "America/New_York",
    { keepLocalTime: true },
  );
  return thisDateTime.toLocaleString(DateTime.DATE_MED);
});
```
