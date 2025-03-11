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

# Pinia Colada

![pinia-colada](./public/pinia-colada.png){.h-64.mx-auto}

## A Cocktail of

## Smooth Data Fetching

## for Better UX

<!--
- My approach to async state management, which includes but is not limited to data fetching
-->

---
layout: cover
---

<h1>
<ruby  class="text-6xl font-sans">
  風<rp>(</rp><rt class="mb-2 text-2xl">fēng</rt><rp>)</rp>水<rp>(</rp><rt class="mb-2 text-2xl">shuǐ</rt><rp>)</rp>
</ruby>
</h1>

<v-clicks>

### "The best space is one in which the arrangement of objects is aligned with the space's flow of energy"{.text-left}

</v-clicks>

_4000 BC Ancient China_

<!--
- Feng shui: 4000 BC Ancient China, "The best space is one in which the arrangement of objects is aligned with the space's flow of energy". In practice, organize the space to make it harmonious and functional. Make the space feel good to be in.
-
-->

---
layout: quote
---

### "\[Tools\] must be positioned in such a way as to not obstruct the surgeon, and also be within easy reach when required. They must be close to the surgeon’s operating hand."

_Hippocrates - Greece 500 B.C_

<!-- 
500 BC Ancient Greece: evidence that ergonomics played a major role in the way tools and workspaces were designed. Hippocrates, the Father of Medicine, describing a Surgeon's workplace: "[Tools] must be positioned in such a way as to not obstruct the surgeon, and also be within easy reach when required. They must be close to the surgeon’s operating hand." user-centric workplaces design.
-->

---
layout: quote
---

### "If the point of contact between the product and people becomes a point of friction, then the designer has failed. If, on the other hand, people are made safer, more comfortable, more desirous of purchase, more efficient—or just plain happier—by contact with the product, then the designer has succeeded."

_Henry Dreyfuss - 1955_

<!--
Henry Dreyfuss, industrial designer

- Much closer to UI than feng shui and hippocrates
- but still how does this apply to web

There is a lot more about UX history, and it's a very interesting topic, I encourage you to read more about it by just searching "History of UX" on Google
-->

---
layout: quote
---

### "I thought Human Interface and usability were too narrow: I wanted to cover all aspects of the person’s experience with a system, including industrial design, graphics, the interface, the physical interaction, and the manual"

_Don Norman (1993)_

<!--
- UX was coined by Don Norman in the 90s
- too recent of a term
- but this concept of measuring how a system performs in terms of experience comes from way back, before a digital era
-->

---
layout: image
backgroundSize: contain
image: '/chrome-blank.png'
---

<!--
- concept of friction and how it relates to browser
- vision of creating a good space from the beginning vs iterating on its flaws (industrial design)
- UX more like iterating
- Past: too idealistic. The reality is not flow
- A browser's main point of contact is the URL bar
  - The first thing you do, even before you see the website, is to wait for the page to load
- Let's take a static website with no javascript
-->

---
layout: full
---

<div class="w-full h-full">
<video ref="video" src="./public/site-navigation.mp4" class="max-w-full max-h-full mx-auto" autoplay muted></video>
</div>

<script setup>
import { onSlideEnter } from '@slidev/client'
import { useTemplateRef } from 'vue'

const video = useTemplateRef('video')
onSlideEnter(() => {
  if (!video.value) {
    return
  }
  video.value.currentTime = 0
  video.value.play()
})
</script>

<!--
- By Henry Dreyfuss' definition, the browser's design has already failed
- what about using it?
-->

---
layout: full
---

<div class="w-full h-full">
<video ref="video" src="./public/link-navigation.mp4" class="max-w-full max-h-full mx-auto" autoplay muted></video>
</div>

<script setup>
import { onSlideEnter } from '@slidev/client'
import { useTemplateRef } from 'vue'

const video = useTemplateRef('video')
onSlideEnter(() => {
  if (!video.value) {
    return
  }
  video.value.currentTime = 0
  video.value.play()
})
</script>

<!--
- Nowadays nobody builds an app like this. In fact, I wouldn't even call it an app, just a website.
- Most interactions in web are async because we communicate with a server
- Caricaturing but all wait times have a negative impact on UX and therefore on the perception of the app.
- I don't need to show you an application video because we all use them every day
- All this async state, data fetching, is a part of applications that con potentially create friction but can also be used to reduce it
- this is the good scenario: static is just assets, we just have to wait a bit for the content
- webapps async also contains errors
-->

---

<!-- the commment -->

## Data fetching is easy 🤡


```vue
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

<!--

- data fetching can be easy but only for simple stuff
- no error management
- no loading state
- No refresh

client cache is for control over a centralized data. We can manually invalidate, refetch

-->

---
layout: image
image: '/distracted-boyfriend-suspense.jpg'
---

<!-- 
Placeholders can be used to show a loading state while the data is being fetched. This can be useful to avoid layout shifts and to keep the user engaged. Personally I prefer to have the placeholder as close as possible to the actual data. Sometimes even inside the component and allow a prop to show it. 
Use a placeholder? <https://zalog.ro/placeholder-loading/>
-->


---
layout: image
backgroundSize: contain
image: '/skeleton-ui.png'
---

<!--
Placeholders can be used to show a loading state while the data is being fetched. This can be useful to avoid layout shifts and to keep the user engaged. Personally I prefer to have the placeholder as close as possible to the actual data. Sometimes even inside the component and allow a prop to show it. 
Use a placeholder? <https://zalog.ro/placeholder-loading/>

The more we use this, the more the users get frustrated with it and the more they will associate frustration with seeing skeletons like these.
-->

---
layout: image
image: '/frustrated-computer.jpg'
---

---
layout: center
---

## Pinia Colada

A layer on top of <logos-pinia></logos-pinia>!

- A query cache via `useQueryCache()` (a <logos-pinia/> store)
- Queries with `useQuery()` and `defineQuery()`
- Mutations with `useMutation()` and `defineMutation()`
- Light but extensible API

<!--
- I like a global and shared access to data -> the query cache
- Precise level of configuration 
- I like light libraries
- I like simplicity over too many abstractions
  - I find it really hard to come back to a project you developed a few years ago but you can't understand anymore where an import came from.
-->

---
layout: image
image: '/baggage-claim.jpg'
---

<!-- 
the perception of speed is more important than speed itself
-->

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

Introducing a slight delay before showing a loading spinner can prevent brief, unnecessary flashes that might draw attention to minor delays.

400ms

<!-- 
https://uxpickle.com/how-long-will-the-busy-spinner-keep-your-user-waiting/?utm_source=chatgpt.com 
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

---
layout: center
---


```vue {5-11|16|18-20|21-25|27-27}{maxHeight:'410px'}
<script setup lang="ts">
import { useQuery } from '@pinia/colada'
import ProductItem from '@/components/ProductItem.vue'

const {
  state: productList,
  asyncStatus,
} = useQuery({
  key: ['products'],
  query: () => fetch('/api/products').then((res) => res.json()),
})
</script>

<template>
  <main>
    <LoadingIndicator v-if="asyncStatus === 'loading'" />

    <div v-if="productList.status === 'error'">
      <ErrorMessage :error="productList.error" />
    </div>
    <div v-else-if="productList.status === 'success'">
      <div v-for="product in productList.data" :key="product.id">
        <ProductItem :product />
      </div>
    </div>
    <!-- v-else-if="productList.status === 'pending'" -->
    <SkeletonLoader v-else />
  </main>
</template>
```

<!--
- The query can be reused in many places and the data is consistent 
- Atomic access to states:
  - status: for the data, which can
  - asyncStatus reflects any loading state
  - Maps well to what we need in the interface
- Discriminated union TS but not even forced to use it
- Notice the order: errors
-->

---

```ts
const {
  state: productList,
  asyncStatus,
} = useQuery({
  key: ['products'],
  query: () => fetch('/api/products').then((res) => res.json()),
})
```

Three different possible `state`s

| `state.status` | `state.data` | `state.error` |
| ------ | ---- | ----- |
| `'pending'` | `undefined` | `null` |
| `'success'` | _defined_ | `null` |
| `'error'` | `undefined` or _defined_ | _defined_ |


---

```ts{*|5,11-13|7,8}
import { useQuery } from '@pinia/colada'

const {
  // main query properties
  state,
  asyncStatus,
  refresh,
  refetch,
  isPlaceholderData,
  // convenient aliases
  error,
  data,
  status,
  // other...
} = useQuery({
  key: ['products'],
  query: () => fetch('/api/products').then((res) => res.json()),
})
```

<!-- 
- state has convenient accesses
- ability to refresh, which doesn't fetch if the data is fresh
- refetch
-->

---
layout: center
---

````md magic-move
```ts
refresh()
refresh()
refresh()
refresh() // just one call!
```
```ts
const p1 = refresh()
refresh()
refresh()
const p2 = refresh()
p1 === p2 // true
await refresh()
```
````

<!-- 
refresh will reuse any ongoing request and will avoid doing one if the data is fresh
in practice, use refresh instead of refetch
-->

---
layout: center
---

## Fresh data

```ts{4}
useQuery({
  key: ['products'],
  query: () => fetch('/api/products').then((res) => res.json()),
  staleTime: 5000, // Data becomes stale after 5s
})
```

<!-- 
By default 5s -> back and forth, no request
most common misconception of client side cache: not about less requests
Opposite: have fresh data as soon as possible
- activating the browser tab will refresh the data
- mounting a component that calls useQuery will also refresh
-->

---
layout: center
---

## Centralized data

```ts{4,9}
const route = useRoute()
// gets the product with all its details
useQuery({
  key: ['products'],
  query: () => fetch('/api/products').then((res) => res.json()),
})

const queryCache = useQueryCache()
const productsEntry = queryCache.getEntries({ key: ['products'], exact: true }).at(0)

const {
  when,
  state,
  asyncStatus,
  active,
  pending,
  stale,
} = productsEntry
```

---
layout: center
---

## Centralized data

```ts
const route = useRoute()
// gets the product with all its details
useQuery({
  key: () => ['products', route.params.productId],
  query: () => getProductById(productId),
})
useQuery({
  key: () => ['products', route.params.productId, { searchResult: true }],
  query: () => getProductSummaryById(productId),
})
```

---
layout: center
---

## Response Times: The Three Important Limits

- **<=100ms**{.font-mono} : same as instant
- **<=1s**{.font-mono} : user stays in flow of thought
- **<=10s**{.font-mono} : context switch

###### [Jacob Nielsen - 1993](https://www.nngroup.com/articles/response-times-3-important-limits/)

<!-- 
- 0.1s: is about the limit for having the user feel that the system is reacting instantaneously, meaning that no special feedback is necessary except to display the result.
- 1s is about the limit for the user's flow of thought to stay uninterrupted, even though the user will notice the delay. Normally, no special feedback is necessary during delays of more than 0.1 but less than 1.0 second, but the user does lose the feeling of operating directly on the data.
- 10s is about the limit for keeping the user's attention focused on the dialogue. For longer delays, users will want to perform other tasks while waiting for the computer to finish, so they should be given feedback indicating when the computer expects to be done. Feedback during the delay is especially important if the response time is likely to be highly variable, since users will then not know what to expect.
-->

---

## Delay spinners

```ts{4-6|8-12}
import { PiniaColada } from '@pinia/colada'
import { PiniaColadaDelay } from '@pinia/colada-plugin-delay'

app.use(PiniaColada, {
  plugins: [PiniaColadaDelay()],
})

useQuery({
  key: ['products'],
  query: () => fetch('/api/products').then((res) => res.json()),
  delay: 400, // delays `asyncStatus`
})
```

---

```vue
<script setup lang="ts">
import { useMutation, useQueryCache } from '@pinia/colada'
import { patchContact } from '@/api/contacts'
import type { Contact } from '@/api/contacts'
import ContactDetail from '@/components/ContactDetail.vue'

const props = defineProps<{ contact: Contact }>()

// we use the query cache to invalidate queries
const queryCache = useQueryCache()

const {
  mutate: updateContact,
  state,
  asyncStatus,
} = useMutation({
  mutation: (contact: Contact) => patchContact(contact),
  onSettled(updatedContact, error, contact) {
    // invalidate the contact list and detail queries
    // they will be refetched automatically if they are being used
    queryCache.invalidateQueries({ key: ['contacts-list'] })
    queryCache.invalidateQueries({ key: ['contacts', contact.id] })
  },
})
</script>

<template>
  <main>
    <LoadingIndicator v-if="asyncStatus === 'loading'" />

    <div v-if="state.error">
      <ErrorMessage :error="state.error" />
    </div>
    <div v-else>
      <ContactDetail
        :contact="props.contact"
        :is-updating="asyncStatus === 'loading'"
        @update="updateContact"
      />
    </div>
  </main>
</template>
```

<!--
Things are going to update in the background. It's consistent but we are not giving feedback to the user
We can show a loading indicator, or a skeleton, or a placeholder, or a combination of them.

- Many options:
  - Indicate that the data is being updated: e.gp a spinner, graying out the info, disabling the form (GitHub). the app is still usable in this time
- All places displaying the info handle the loading locally, can be a spinner, can be a grayed out version of the data.
- 
-->

---

# Query Cache

- Pinia store that centralizes all the queries
  - Powerful plugin API based on `$onAction()`

<!--
It's often forgotten that Pinia is not just a global state + devtools. The plugin API is what makes it really powerful.
Actions acts as events that you can interact with. Fetching, invalidating, cancelling, they all trigger different actions
-->

```ts
import { PiniaColada } from '@pinia/colada'
import { PiniaColadaDelay } from '@pinia/colada-plugin-delay'

app.use(PiniaColada, {
  plugins: [
    PiniaColadaDelay(),
  ],
})
```

```ts {*|3}
export function PiniaColadaDelay(options?: PiniaColadaDelayOptions): PiniaColadaPlugin {
  return ({ queryCache, scope }) => {
    queryCache.$onAction(({ name, after }) => {
      if (name === 'create') {
        after((entry) => {
          const delay = entry.options?.delay ?? options?.delay ?? 200
          scope.run(() => {
            const isDelaying = shallowRef(false)
            entry.ext.isDelaying = isDelaying
            if (!delay) return

            const initialValue = entry.asyncStatus.value
            entry.asyncStatus = customRef<AsyncStatus>((track, trigger) => {
              let value = initialValue
              let timeout: ReturnType<typeof setTimeout> | undefined
              return {
                get() {
                  track()
                  return value
                },
                set(newValue) {
                  clearTimeout(timeout)
                  if (newValue === 'loading') {
                    isDelaying.value = true
                    timeout = setTimeout(() => {
                      isDelaying.value = false
                      value = newValue
                      trigger()
                    }, delay)
                  } else {
                    isDelaying.value = false
                    value = newValue
                    trigger()
                  }
                },
              }
            })
          })
        })
      }
    })
  }
}

interface PiniaColadaDelayOptions {
  delay?: number | false
}

declare module '@pinia/colada' {
  interface UseQueryOptions<TResult, TError> extends PiniaColadaDelayOptions {}

  interface UseQueryEntryExtensions<TResult, TError> {
     */
    isDelaying: ShallowRef<boolean>
  }
}
```

---


Predicting the future

- Pre fetching
- Optimistic updates

<!--
the surgeon has people around that know the process and can provide the tools before they are needed
-->

---


Know your audience

<!-- 
Spacejam example might feel good because of nostalgia but can also feel like a horrendous experience

Loading times are not the same if your application is ran in an internal network, always on desktops with a good internet connection than if it's ran on mobile devices on the subway.
-->

---


STOP
STOOOOOOOOP

---
layout: cover
---

# Great User Experience

<!--
Initial feedback about if it was easy to use. Then start asking more questions and they will start commenting on the looks of the application very quickly.
- feedback varies between users
- they all have different feedback on visuals
- ux can be subjective
-->

---
layout: quote
---

# Halo Effect

People instinctively trust and favor things that look good, whether it's a person, a product, or an interface

<!--
- Applications, like anything else suffers or benefits from the halo effect
- well documented cognitive bias
- Hire good designers
-->

---
layout: quote
---

### Users form judgments about website aesthetics in as little as **50 milliseconds**, influencing their overall perception of usability and trustworthiness.

_Lindgaard et al. (2006)_

<!--
- research in psychology -> interesting results
- one I find interesting
- funny: they form a perception before js is even loaded
- UX also includes subjective features
-->
