





---
layout: center
---

## Hierarchical data

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
