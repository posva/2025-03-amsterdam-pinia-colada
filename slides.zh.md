---
theme: "@posva/slidev-theme"
# random image from a curated Unsplash collection by Anthony
# background: https://cover.sli.dev
title: "Pinia Colada：流畅数据获取的调和之道，打造更好的用户体验"
info: |
  ## Pinia Colada

  流畅数据获取的调和之道，打造更好的用户体验

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
htmlAttrs:
  dir: ltr
  lang: zh
---

<div class="flex flex-col items-start h-full pt-16" >

<img class="w-32 h-32 mb-4 rounded-full" src="/posva.jpeg" alt="eduardo avatar">

<div class="text-left">

<span class="my-0 font-serif text-4xl font-bold">Eduardo San Martin Morote</span>
<br>
<span class="my-0 font-serif text-xl font-light">前端极客</span>
<br>
<span><logos-pinia />、<logos-vue /> Router、<img class="inline-block -translate-y-[5px]" style="height: 1.5em;" src="/vuefire.svg"> 作者</span>

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

![pinia-colada](/pinia-colada.png){.h-64.mx-auto}

## 调和之道

## 流畅数据获取

## 更好的用户体验

<!--
- refreshing approach to async state management
- how to use it to improve your UX
- before I wanna talk history of UX
- a few years back
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

### "最佳的空间是那些物品排列与空间能量流动相和谐的地方"

</v-clicks>

_公元前 4000 年 中国古代_

<!--
- did I say a few years, sorry meant a few thousands
- 4000 bc, no interfaces, no digital
- UX couldn't exist, but idea did
- Ergonomics
- Feng shui: 4000 BC Ancient China, "The best space is one in which the arrangement of objects is aligned with the space's flow of energy"
- organize the space to make it harmonious and functional. Make the space feel good to be in.
- ergonomic about the space
-->

---
layout: cover
background: '/hippocrates.jpeg'
---

### "（工具）必须以不妨碍外科医生的方式放置，并且在需要时能够轻松取到。它们必须靠近外科医生的操作手。" {.text-white.bg-black/50.p-2.rounded-xl}

_希波克拉底 - 希腊 公元前 500 年_

<!--
- huh · po · kruh · teez, father of medicine
- played major role in the way tools and workspaces designed
- describing surgeon's workplace
-  "Tools must be positioned in such a way as to not obstruct the surgeon, and also be within easy reach when required. They must be close to the surgeon's operating hand."
- From space harmonity
- user-centric approach
- Space optimized for a surgeon
-->

---
layout: cover
background: '/henry-dreyfuss-bg.jpg'
---

### "如果产品与人之间的接触带来摩擦，那么设计是失败的。反之，如果人们通过与产品的接触变得更安全、更舒适、更有购买欲望、更高效，或者单纯地更快乐，那么设计师就成功了。" {.text-white.bg-black/50.p-2.rounded-xl}

_Henry Dreyfuss - 1955_

<!--
- Henry Dreyfuss, industrial designer, 1955
- If the point of contact between the product and people becomes a point of friction, then the designer has failed. If, on the other hand, people are made safer, more comfortable, more desirous of purchase, more efficient—or just plain happier—by contact with the product, then the designer has succeeded
- Much closer to UI than feng shui and hippocrates
- 1st time we talk about failure
- before: as if one shot to get it right
- adapt? iterating?
- much closer to UI
- flow / friction
-->

---
layout: cover
background: '/donald-norman.jpg'
---

### "我觉得人机界面和可用性太狭隘了：我想要涵盖用户体验系统的所有方面，包括工业设计、图形设计、界面、物理交互和手册" {.text-white.bg-black/50.p-2.rounded-xl}

_Don Norman (1993)_

<!--
- History goes on, but stop in 1993
- UX was coined by Don Norman in the 90s
- There is a lot more about UX history, and it's a very interesting topic, I encourage you to read more about it by just searching "History of UX" on Google
- Go back to friction point and apply to a browser
-->

---
layout: image
backgroundSize: contain
image: '/chrome-blank.png'
---

<!--
- Past: too idealistic. The reality is not flow
- 1955 idea of friction
- A browser's main point of contact is full of friction
- the URL bar
- The first thing you do, even before you see the website, is to wait for the page to load
- Let's take a static website with no javascript
-->

---
layout: full
---

<div class="w-full h-full">
<video ref="video" src="/site-navigation.mp4" class="max-w-full max-h-full mx-auto" autoplay muted></video>
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
- as we load, we need to wait for things to appear
- By Henry Dreyfuss' definition, the browser's design has already failed
- notice how did you feel when the website loaded?
- who knew this website? website for a movie called spaced jam from 1996, 1 year after initial release of JS, 1y before the creation of the JS standard
- was it a positive feeling? raise
- for who was it negative?
- we haven't used the website, we already create an idea of it.
- studies show we form idea the first 50ms we see an interface. before the js loads for every application
- cognitive bias: halo effect. the way the space flows, still affects us (风水)
- So no, the browser design hasn't failed us because the friction here is not avoidable
- in fact, using the website becomes even worse
-->

---
layout: full
---

<div class="w-full h-full">
<video ref="video" src="/link-navigation.mp4" class="max-w-full max-h-full mx-auto" autoplay muted></video>
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
- all interactions make the user wait
- Nowadays nobody builds an app like this. In fact, just a website.
- async because we communicate with a server
- no need to show a video, you likely used app in the past few days
- likely had a frustration experience
- loading that hangs
- things that load but then show blank content
- that small stress of is it going work? I clicked back, did I break the form? Will I have to start my order all over again?
- That's the par that interests me
- Aesthetics subjective, hire a good designer
- managing loading state, errors, consistent way to make your app feel better
-->

---

<!-- the commment -->

## 数据获取很简单 🤡


```vue
<script setup lang="ts">
import { fetchRecipeList, type Recipe } from '@/api'

const recipeList = shallowRef<Recipe[]>([])
onMounted(async () => {
  recipeList.value = await fetchRecipeList()
})
</script>

<template>
  <ul>
    <RecipeCard v-for="recipe in recipeList" :key="recipe.id" :recipe />
  </ul>
</template>
```

<!--
- but worse than static because no loading
- you might be thinking you can use suspense and stick a skeleton ui
-->

---
layout: image
image: '/distracted-boyfriend-suspense.jpg'
---

<!--
Placeholders can be used to show a loading state while the data is being fetched. This can be useful to avoid layout shifts and to keep the user engaged.
-->

---
layout: image
backgroundSize: contain
image: '/skeleton-ui.png'
---

<!--
- so widely used, that some app used it wrong
- yet so similar for the brain
- if the placeholder stays up a bit too long: is the app broken?

Something I do myself: if skeleton stays too long, I freak out and my developer instincts go off: I open the devtools and search for red
-->

---
layout: image
image: '/frustrated-computer.jpg'
---

<!--
- there is nothing worse in UX that when we feel less efficient
- includes unexpected errors
- not feeling in control
- no feedback loop
- handle errors properly
- but unexpected errors always create frustration, but it's better to show something than nothing at all
- our goal is to reduce the wait time
-->

---
layout: center
---

# 减少等待时间

<v-clicks>

- 让我们的异步操作更快
- 更早地开始执行
- 让它们_感觉起来_更快

</v-clicks>

<!--
- to keep in flow
- that's the gist of it
- I'm going to show you some tricks
- focus today on these points with pinia colada
-->

---
layout: center
---

## Pinia Colada

基于 <logos-pinia></logos-pinia> 构建的 Vue 插件！

- 通过 `useQueryCache()` 提供查询缓存（一个 <logos-pinia/> store）
- 通过 `useQuery()`、`defineQueryOptions` 和 `defineQuery()` 进行查询
- 通过 `useMutation()` 和 `defineMutation()` 进行变更
- 轻量但可扩展的 API

<!--
- what is it? Vue plugin, layer on top of pinia
- main parts of it
- query cache, simple client side cache, pinia store, centralize
- Queries are the async operations that read data. List of products, search result, some user's profile
- Mutations opposite, async operations that write data to server
- It's similar to GET/POST, but in practice a search can be a post
- light: ~3kb, lean an extensible API to adapt to your needs. important
-->

---
layout: center
---

```vue {5-11|9|10|6-7|16|18-20|21-25|27-27}{maxHeight:'410px'}
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
- queries first and most important part
- [click]key how stored in cache
- The query can be reused in many places and the data is consistent 
- [click] query fn
- [click] get among other things, state, asyncStatus
- asyncStatus reflects any loading state: interesting = automatically refetches
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

三种不同的 `state`

| `state.status` | `state.data` | `state.error` |
| ------ | ---- | ----- |
| `'pending'` | 无 | 无 |
| `'success'` | 有值 | 无 |
| `'error'` | 可能有值 | 有错误 |

<!--
- works well with discriminated unions in TS
- not forced to use
-->

---

```ts{*|5,11-13|7,8|16}
import { useQuery } from '@pinia/colada'

const {
  // 主要查询属性
  state,
  asyncStatus,
  refresh,
  refetch,
  isPlaceholderData,
  // 便捷别名
  error,
  data,
  status,
  // 其他...
} = useQuery({
  key: ['products'],
  query: () => fetch('/api/products').then((res) => res.json()),
})
```

<!-- 
- state has convenient accesses
- ability to refresh, which doesn't fetch if the data is fresh
- refetch
- on the surface, seems just like loading and error
- but what makes it so special?
- the key links them together
- can be called in many places, still just one source of data
-->

---
layout: center
---

````md magic-move
```ts
refresh()
refresh()
refresh()
refresh() // 只会发起一次调用！
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
- same with refreshes
- refresh will reuse any ongoing request and will avoid doing one if the data is fresh
- in practice, use refresh instead of refetch
- inconsistent updates of data create confusion and users loose trust
- centralized place for data = consistent state across your app
- ex: change avatar in user and it doesn't change in the navbar
-->

---
layout: center
---

## 集中化数据

```ts{4,9}
const route = useRoute()
// 获取产品及其所有详细信息
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

<!--
- by linking things though key
- access to the cache entries
- client cache not about replacing the server cache
- not reducing calls but making more at the right time
-->

---
layout: center
---

## 查询缓存

```vue
<script setup lang="ts">
import { useQueryCache } from '@pinia/colada'

const queryCache = useQueryCache()
</script>
```

<!--
- it's a client side cache
- why if on server
  - not about doing less requests
  - actually about doing more requests but at the appropriate time
-->

---
layout: center
---

## 最新数据

```ts{*|4}
useQuery({
  key: ['products'],
  query: () => fetch('/api/products').then((res) => res.json()),
  staleTime: 5000, // 数据在 5 秒后过期
})
```

<!--
- concept of fresh vs stale data (like in cache)
- fresh data: is up to date
- stale data: is not up to date and should be prefetched
- noticed query has no argument
- automatically triggers a refetch if the data is stale
  - on foc
  - mount component with useQuery
- let the cache refetch for you
- hint it about outdated data
- reduce wait times a bit but do more
-->

---
layout: image
image: '/baggage-claim.jpg'
---

<!--
- tell story about baggage claim in Huston
- the perception of speed is more important than speed itself
  - Make the user not realize they are waiting
- how applies to web?
-->

---
layout: center
---

## 响应时间：三个重要的限制

- **<=100ms**{.font-mono} : 几乎是一瞬间
- **<=1s**{.font-mono} ：用户操作不易被打断
- **>=10s**{.font-mono} : 会感到上下文切换

###### [Jacob Nielsen - 1993](https://www.nngroup.com/articles/response-times-3-important-limits/)

<!--
- 0.1s: is about the limit for having the user feel that the system is reacting instantaneously, meaning that no special feedback is necessary except to display the result.
- 1s is about the limit for the user's flow of thought to stay uninterrupted, even though the user will notice the delay. Normally, no special feedback is necessary during delays of more than 0.1 but less than 1.0 second, but the user does lose the feeling of operating directly on the data.
- 10s is about the limit for keeping the user's attention focused on the dialogue. For longer delays, users will want to perform other tasks while waiting for the computer to finish, so they should be given feedback indicating when the computer expects to be done. Feedback during the delay is especially important if the response time is likely to be highly variable, since users will then not know what to expect.
- my API never gonna take 10s. Until you introduce AI
-->

---
layout: center
---

## spinner

```ts{4-6|8-12}
import { PiniaColada } from '@pinia/colada'
import { PiniaColadaDelay } from '@pinia/colada-plugin-delay'

app.use(PiniaColada, {
  plugins: [PiniaColadaDelay()],
})

useQuery({
  key: ['products'],
  query: () => fetch('/api/products').then((res) => res.json()),
  delay: 400, // 延迟 `asyncStatus`
})
```

<!--
- many ways of applying this
- Plugins later
- Plays with the perception of speed
-->

---
layout: full
---

<div class="w-full h-full">
<video ref="video" src="/demo-delay.mp4" class="max-w-full max-h-full mx-auto" autoplay muted></video>
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

---
layout: full
---

<div class="w-full h-full">
<video ref="video" src="/demo-no-delay.mp4" class="max-w-full max-h-full mx-auto" autoplay muted></video>
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

---
layout: center
---

## 变更操作

```vue {*|9|5-7|20}{maxHeight:'410px'}
<script setup lang="ts">
import { useMutation } from '@pinia/colada'

const {
  mutate: createTodo,
  status,
  asyncStatus,
} = useMutation({
  mutation: (todoText: string) =>
    fetch('/api/todos', {
      method: 'POST',
      body: JSON.stringify({ text: todoText }),
    }),
})

const todoText = ref('')
</script>

<template>
  <form @submit.prevent="createTodo(todoText)">
    <input v-model="todoText">
    <button :disabled="asyncStatus === 'loading'">
      添加待办事项
    </button>
  </form>
</template>
```

<!--
- another way of playing with perception of speed
- mutate fn only required
- gives access to the state, exactly like a query
- does not execute automatically, so it can take arguments
- most apps have both, queries and mutations
- key is to use them together, how?
-->

---
layout: center
---

## 变更操作

```vue{*|18-22}{maxHeight:'410px'}
<script setup lang="ts">
import { useMutation, useQueryCache } from '@pinia/colada'
import { patchContact } from '@/api/contacts'
import type { Contact } from '@/api/contacts'
import ContactDetail from '@/components/ContactDetail.vue'

const props = defineProps<{ contact: Contact }>()

// 我们使用查询缓存来重置查询
const queryCache = useQueryCache()

const {
  mutate: updateContact,
  state,
  asyncStatus,
} = useMutation({
  mutation: (contact: Contact) => patchContact(contact),
  onSettled(updatedContact, error, contact) {
    // 重置联系人列表和详情查询
    // 如果它们正在使用，会自动重新获取
    queryCache.invalidateQueries({ key: ['contacts'], exact: true })
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
- while queries are more common, mutations is where there is  more risk to create friction
- more likely errors
- a place full of opportunities
- know what the user is going to do next, what it's going to fetch
- so we can tell pinia colada, these queries needs to be prefetched
- that's what invalidates does, it cancels any ongoing queries, mark them as stale, and if they are active, fetches them
- mutation still finishes before the queries are loaded, but we can even await the invalidations
- if the queries used in the background, their loading state will reflect that, they will keep showing the old state while fetching
- how to show up to you:
  - Indicate that the data is being updated: e.gp a spinner, graying out the info, disabling the form (GitHub). the app is still usable in this time
- I recommend not showing the loading state too prominently, it shouldn' attract user's attention
- graying out is no to noticeable
-->

---
layout: center
---

## 预测未来

<v-clicks>

- 预获取
- 乐观更新

</v-clicks>

<!--
- in a way, we try to predict
- the surgeon has people around that know the process and can provide the tools before they are needed
- Optimistic updates: when mutating server state, we can update the client state before the server responds
-->

---
layout: center
---

# 🪄 [todos.nuxt.dev](https://todos.nuxt.dev/optimistic-todos){.font-mono}

<!--
- show how it's instant
-->

---
layout: center
---

```ts {*|2-12|14|16|17-31|33|35,38|39-47|50-53|55-75|59-62}{maxHeight:'410px'}
const { mutate: addTodo } = useMutation({
  mutation: (title: string) => {
    if (!title.trim()) throw new Error('标题是必需的')

    return $fetch('/api/todos', {
      method: 'POST',
      body: {
        title,
        completed: 0,
      },
    })
  },

  onMutate(title) {
    // 让用户立即输入新的待办事项！
    newTodo.value = ''
    const oldTodos = queryCache.getQueryData<Todo[]>(['todos']) || []
    const newTodoItem = {
      title,
      completed: 0,
      // 使用负数 id 来区分它们和服务器返回的
      id: -Date.now(),
      createdAt: new Date(),
      userId: user.value!.id
    } satisfies Todo
    // 我们使用 newTodos 来检查缓存一致性
    const newTodos = [
      ...oldTodos,
      newTodoItem
    ]
    queryCache.setQueryData(['todos'], newTodos)

    queryCache.cancelQueries({ key: ['todos'], exact: true })

    return { oldTodos, newTodos, newTodoItem }
  },

  onSuccess(todo, _, { newTodoItem }) {
    // 使用服务器返回的信息更新待办事项
    // 由于我们要重置查询，这允许我们渐进式地
    // 更新待办事项列表，即使用户添加得很快
    const todoList = queryCache.getQueryData<Todo[]>(['todos']) || []
    const todoIndex = todoList.findIndex(t => t.id === newTodoItem.id)
    if (todoIndex >= 0) {
      queryCache.setQueryData(['todos'], todoList.toSpliced(todoIndex, 1, todo))
    }
    toast.add({ title: `待办事项 "${todo.title}" 已创建。` })
  },

  onSettled() {
    // 变更后始终重新获取待办事项
    queryCache.invalidateQueries({ key: ['todos'] })
  },

  onError(err, _title, { oldTodos, newTodos }) {
    // 如果 onMutate 出错，oldTodos 可能是 undefined
    // 我们还要检查 oldTodos 是否仍在缓存中
    // 因为缓存可能已被另一个查询更新
    if (newTodos != null && newTodos === queryCache.getQueryData(['todos'])) {
      queryCache.setQueryData(['todos'], oldTodos)
    }

    if (isNuxtZodError(err)) {
      // eslint-disable-next-line @typescript-eslint/no-explicit-any
      const title = (err as any).data.data.issues
        .map((issue: { message: string }) => issue.message)
        .join('\n')
      toast.add({ title, color: 'red' })
    }
    else {
      console.error(err)
      toast.add({ title: '意外错误', color: 'red' })
    }
  }
})
```

<!-- 
- that was a lot of code! Can we make it less?
- yes, with conventions in a project
- I wouldn't recommend it too much because it's great to have a code that can be read and adapted
- not blocking
- but you can do it with plugins
-->

---
layout: center
---

# 查询缓存

基于 <logos-pinia /> `$onAction()` 的强大插件 API

<!--
It's often forgotten that Pinia is not just a global state + devtools. The plugin API is what makes it really powerful.
Actions acts as events that you can interact with. Fetching, invalidating, cancelling, they all trigger different actions
-->

```ts {*|3|4|7-9|13|45-54}{maxHeight:'410px'}
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
    isDelaying: ShallowRef<boolean>
  }
}
```

---
layout: center
---

## Pinia Colada

- 避免过快显示加载状态
- 使用集中化数据保持状态一致
- 一旦知道数据发生变化就立即失效查询
- 使用乐观更新让应用感觉更快

<v-clicks>

- 生产力爆棚！！ 👨‍💻

</v-clicks>

![pinia-colada](/pinia-colada.png){.h-64.mx-auto}

<!--
- No silver bullet
- perception of speed goes beyond pinia: page transitions for long requests
-->

---
layout: end
---

# 谢谢
