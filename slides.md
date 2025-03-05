---
theme: "@posva/slidev-theme"
# random image from a curated Unsplash collection by Anthony
background: https://cover.sli.dev
title: "Pinia Colada: A Cocktail of Smooth Data Fetching for Better UX"
info: |
  ## Pinia Colada

  A Cocktail of Smooth Data Fetching for Better UX

  (c) 2025 Eduardo San Martin Morote

  [esm.dev](https://esm.dev)
# apply unocss classes to the current slide
class: text-center
transition: view-transition
transition-duration: 1000ms
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
# transition: slide-left
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true
---

<div class="flex flex-col items-start h-full pt-16" >

<img class="w-32 h-32 mb-4 rounded-full" src="/posva.jpeg" alt="eduardo avatar">

<div class="text-left">

<span class="my-0 font-serif text-4xl font-bold">Eduardo San Martin Morote</span>
<br>
<span class="my-0 font-serif text-xl font-light">Frontend Nerd</span>
<br>
<span><logos-pinia />, <logos-vue /> Router, <img class="inline-block -translate-y-[5px]" style="height: 1.5em;" src="/vuefire.svg"> Author</span>

</div>

<span><carbon-logo-github /> <carbon-logo-x /> [@posva]{.font-mono} <carbon-logo-bluesky /> [@esm.dev]{.font-mono}</span>

</div>

<!--
Hello everyone! I'm Eduardo, or posva on GitHub and Twitter.

I'm the author of pinia, Vue Router, and other vue-related libraries like VueFire.

I have been part of the core team for a very long time, I think it's 8 years now.

During this journey I have encountered many different problems and I have tried to solve most of them.
Except for one, Data Fetching.
-->

---
layout: cover
---

# Data Fetching
# 😈 😈 😈

---

# Welcome to Slidev

Presentation slides for developers

<div @click="$slidev.nav.next" class="mt-12 py-1" hover:bg="white op-10">
  Press Space for next page <carbon:arrow-right />
</div>

<div class="abs-br m-6 text-xl">
  <button @click="$slidev.nav.openInEditor" title="Open in Editor" class="slidev-icon-btn">
    <carbon:edit />
  </button>
  <a href="https://github.com/slidevjs/slidev" target="_blank" class="slidev-icon-btn">
    <carbon:logo-github />
  </a>
</div>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---

# What is Slidev?

Slidev is a slides maker and presenter designed for developers, consist of the following features

- 📝 **Text-based** - focus on the content with Markdown, and then style them later
- 🎨 **Themable** - themes can be shared and re-used as npm packages
- 🧑‍💻 **Developer Friendly** - code highlighting, live coding with autocompletion
- 🤹 **Interactive** - embed Vue components to enhance your expressions
- 🎥 **Recording** - built-in recording and camera view
- 📤 **Portable** - export to PDF, PPTX, PNGs, or even a hostable SPA
- 🛠 **Hackable** - virtually anything that's possible on a webpage is possible in Slidev
<br>
<br>

Read more about [Why Slidev?](https://sli.dev/guide/why)

<!--
You can have `style` tag in markdown to override the style for the current page.
Learn more: https://sli.dev/features/slide-scope-style
-->

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

<!--
Here is another comment.
-->
