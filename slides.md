---
theme: "@posva/slidev-theme"
# random image from a curated Unsplash collection by Anthony
# background: https://cover.sli.dev
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

<span><carbon-logo-github /> <carbon-logo-x /> [@posva]{.font-mono} <logos-bluesky /> [@esm.dev]{.font-mono}</span>

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

<h1>
<ruby  class="text-6xl font-sans">
  風<rp>(</rp><rt class="mb-2 text-2xl">fēng</rt><rp>)</rp>水<rp>(</rp><rt class="mb-2 text-2xl">shuǐ</rt><rp>)</rp>
</ruby>
</h1>


---
layout: cover
---

# Pinia Colada

## A Cocktail of

## Smooth Data Fetching

## for Better UX

<!--
TODO: logo on the side or something to make it look better
-->

---


````md magic-move
```vue{*|4|5-7|12}
<script setup lang="ts">
import { fetchRecipeList, type Recipe } from "@/api";

const recipeList = shallowRef<Recipe[]>([]);
onMounted(async () => {
  recipeList.value = await fetchRecipeList();
});
</script>

<template>
  <ul>
    <RecipeCard v-for="recipe in recipeList" :key="recipe.id" :recipe />
  </ul>
</template>
```

```vue{*|4-5,12}
<script setup lang="ts">en
import { fetchRecipeList, type Recipe } from "@/api";

const recipeList = shallowRef<Recipe[]>([]);
recipeList.value = await fetchRecipeList();
</script>

<template>
  <ul>
    <RecipeCard v-for="recipe in recipeList" :key="recipe.id" :recipe />
  </ul>
</template>
```
````

<p v-click.hide="4">Simple Client side only</p>

<p v-click="+4" v-click.hide="6">Suspense</p>

<!--

Classic SPA fetching, only on client. User clicks on recipe, comes back, reloads again (most of the time cached by the server).
and so they think, I don't need a client side cache. But that's not what a client side cache is for.

client cache is for control over a centralized data. We can manually invalidate, refetch

-->

---

<!--
Suspense moves the responsibility of loading and errors to the parent component. For errors that
-->

````md magic-move
```vue
<script lang="ts" setup>
import { searchContacts } from "@/api/contacts";
import { useRouteQuery } from "@vueuse/router";
import { shallowRef, watch } from "vue";

const searchText = useRouteQuery("search", "", { mode: "push" });

const searchResult = shallowRef<Awaited<ReturnType<typeof searchContacts>>>();
watch(
  searchText,
  async () => {
    searchResult.value = await searchContacts(searchText.value, {});
  },
  { immediate: true },
);
</script>
```

```vue
<script lang="ts" setup>
import { searchContacts } from "@/api/contacts";
import { useRouteQuery } from "@vueuse/router";
import { shallowRef, watch } from "vue";

const searchText = useRouteQuery("search", "", { mode: "push" });

const searchResult = shallowRef<Awaited<ReturnType<typeof searchContacts>>>(
  await searchContacts(searchText.value),
);
watch(searchText, async () => {
  searchResult.value = await searchContacts(searchText.value);
});
</script>
```
````

```vue
<script setup lang="ts">
en;
</script>

<template>
  <Suspense>
    <template #default>
      <ul>
        <RecipeCard v-for="recipe in recipeList" :key="recipe.id" :recipe />
      </ul>
    </template>
    <template #error>
      <p>Failed to load recipes</p>
      <button @click="retry()">Retry</button>
    </template>
    <template #loading>
      <p>Loading...</p>
    </template>
  </Suspense>
</template>
```

---

Use a placeholder? <https://zalog.ro/placeholder-loading/>

Placeholders can be used to show a loading state while the data is being fetched. This can be useful to avoid layout shifts and to keep the user engaged. Personally I prefer to have the placeholder as close as possible to the actual data. Sometimes even inside the component and allow a prop to show it.

```vue-html
<RecipeCard :loading="asyncState === 'loading'" :recipee />
```

---
layout: image
image: '/baggage-claim.jpg'
---

---
layout: image
backgroundSize: contain
image: '/sims-2-loading.webp'
---


<!--
- Entertain the user reading
-->

---
layout: image
image: '/interactive-floor-projection.jpg'
---

<!--
A different public. Useful in different ways
- A moment of rest for the parents, or time to check where to have lunch
- Place it nearby the food court, allows people to wait until free spot
-->

---

Know your audience

<!-- 
Loading times are not the same if your application is ran in an internal network, always on desktops with a good internet connection than if it's ran on mobile devices on the subway.
-->

---

Introducing a slight delay before showing a loading spinner can prevent brief, unnecessary flashes that might draw attention to minor delays.

400ms

<!-- 
https://uxpickle.com/how-long-will-the-busy-spinner-keep-your-user-waiting/?utm_source=chatgpt.com 
-->

---

2018 Google study about bounce rate

<!-- 
https://www.thinkwithgoogle.com/marketing-strategies/app-and-mobile/mobile-page-speed-new-industry-benchmarks/
-->


---

- Know your audience
- Get creative

<!--
No silver bullet
Why do it? Because a perception slower wait times, creates a better experience.
-->

---

Modern apps: lots of streams of data with AI
Probably not for Pinia Colada
