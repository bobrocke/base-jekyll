---
title: Settling on TailwindCSS
date: 2025-04-08
lastmod:
summary:
description:
draft: true
categories: [Web Development]
tags: [CSS]
---

While experimenting with various [static site generators](2025-03-14-moving-from-wordpress), I've also been learning about [Bulma](https://bulma.io/) (a traditional CSS framework) and [TailwindCSS](https://tailwindcss.com/) (a 'new style' utility CSS framework). They come at the idea of a CSS framework from two very different perspectives, and if you've seen the Internet discussions, you'll know that opinions are decidedly mixed.

<!--more-->

A typical case is styling a button. Bulma let's you do it simply:

```html
<button class="button">Button</button>
```

and you get a reasonably styled button. It's easy to be sure all your buttons look the same by using the same class on all of them.

TailwindCSS goes at it from another direction. You could style a button like this:

```HTML
<button class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 me-2 mb-2 dark:bg-blue-600 dark:hover:bg-blue-700 focus:outline-none dark:focus:ring-blue-800"> Button </button>
```

Behind Bulma's simple `button` class is plenty of CSS scattered in many places across `bulma.css`:

```CSS
margin: 0;
font-family: var(--bulma-body-family);
cursor: pointer;
outline-color: hsl(var(--bulma-focus-h), var(--bulma-focus-s), var(--bulma-focus-l));
outline-offset: var(--bulma-focus-offset);
outline-style: var(--bulma-focus-style);
outline-width: var(--bulma-focus-width);
.button.is-primary {
  --bulma-button-h: var(--bulma-primary-h);
  --bulma-button-s: var(--bulma-primary-s);
  --bulma-button-l: var(--bulma-primary-l);
  --bulma-button-background-l: var(--bulma-primary-l);
  --bulma-button-border-l: var(--bulma-primary-l);
  --bulma-button-border-width: 0px;
  --bulma-button-color-l: var(--bulma-primary-invert-l);
  --bulma-button-outer-shadow-a: 0;
}
```

And there's lots more. It's easy to get started on a project by using Bulma's classes on all the things. But when you step back and look, it looks like ... _Bulma_. You need to optimize and customize. So off you go to the inspector and find what to override for this element, that element, and the other element. Always hoping not to enter CSS class specificity hell.

TailwindCSS looks bad at the start. What's up with all those classes!? But if you need to tweak something, it's all there in front of you. Does this element need a little more bottom margin in this one place? Change `mb-2` to `mb-4` and you're done. If a Bulma element needs a change in just this one place, you need to write another class. And make the context switch going to another file, in another pane, written in another language.

But being consistent with TailwindCSS takes some effort. Was it `text-red-600` I've been using, or was it `text-red-400`? All the `<button>`s need the same string of classes pasted in. Bulma just needs `class="button"` on all the `<button>`s.

A problem in many situations is that some of a page's content is generated from a markdown file. The site author won't have access to the HTML in order to style it in the normal way. Both Bulma and TailwindCSS have classes, `content` for Bulma and `prose` for TailwindCSS, that can be applied to a `<div>` enclosing the markdown output. Something like:

```HTML
<div class="prose">
  {{ markdown }}
</div>
```

Those classes can then style the HTML tags output by the markdown renderer. TailwindCSS allows its `prose` class to be extended in a number of ways, for example `prose-a:text-blue-600` and `prose-a:hover:text-red-600`. Similar modifiers work for Bulma, but there are fewer available. If you need more, it's back to CSS overrides or new classes.
