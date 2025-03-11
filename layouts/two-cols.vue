<!--
  Usage:

```md
---
layout: two-cols
---

# Left

This shows on the left

::right::

# Right

This shows on the right
```

-->

<script setup lang="ts">
const { noBorder, class: className, header, ratio = 1 } = defineProps<{
  class?: string
  header?: string
  noBorder?: boolean
  ratio?: number
}>()
</script>

<template>
  <div class="slidev-layout">
    <h2 v-if="header" v-html="header"></h2>
    <div class="grid w-full h-full layout-container two-columns py-4">
      <div class="col-left pr-4" :class="className">
        <slot />
      </div>
      <div
        class="col-right border-l pl-4 border-gray-500 border-opacity-50"
        :class="[className, { 'border-opacity-0': noBorder }]"
      >
        <slot name="right" />
      </div>
    </div>
  </div>
</template>

<style scoped>
.layout-container {
  grid-template-columns: minmax(0, v-bind('ratio + "fr"')) minmax(0, 1fr);
}
</style>
