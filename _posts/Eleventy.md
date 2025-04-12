---
title: Learning About Eleventy
date: 2025-03-01
lastmod: 2025-03-03
tags: [""]
description:
summary:
draft:
datemodified:
---

I finished moving this blog from WordPress to Hugo and read about a number of other static site generators before I chose Hugo. Hugo is very popular and very capable, but it does have its oddities. Eleventy, or 11ty, is another very popular system and I felt as if I needed to understand it better before absolutely standing with Hugo.

<!-- more -->

So I'm re-writing my blog with 11ty---no better way to learn about it.

11ty documentation is solid, if a little short on API details, but the search feature is pretty good. There doesn't seem to be all that much independent reference material on the web.

While I'm experimenting, I tried out the Bulma CSS library after having used Tailwind with Hugo. My impressions will have to wait for another post, suffice it to say that I'm continuing to work with 11ty using Tailwind.

Hugo comes 'out of the box' with more features than 11ty; you add the ones you need as plugins from node modules. I have these:

```json
"dependencies": {
  "@11ty/eleventy": "^3.0.0",
  "@11ty/eleventy-plugin-syntaxhighlight": "^5.0.0",
  "@jgarber/eleventy-plugin-markdown": "^2.0.1",
  "@tailwindcss/postcss": "^4.0.17",
  "@tailwindcss/typography": "^0.5.16",
  "cssnano": "^7.0.6",
  "flowbite": "^3.1.2",
  "postcss": "^8.5.3",
  "tailwindcss": "^4.0.17"
},
```

Almost all of them are related to getting Tailwind, and the Tailwind component library [Flowbite](https://flowbite.com/), working.

Dates in 11ty are hard. The default is UTC time and it took me a while to figure out how to change those dates into my local time and format them in a friendly way. I got some of the way by trial and error, but I eventually got stuck. Stuck until I found [the solution here](https://www.eladnarra.com/blog/2024/dates-and-eleventy/).
