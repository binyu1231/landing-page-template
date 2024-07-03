<script lang="ts" setup>
import { useEventListener } from '@vueuse/core';
import { defineOptions } from 'vue';

defineOptions({ name: 'demo-scroll' })

const scrollViewRef = ref<HTMLDivElement>()
const d = reactive({
  start: 0,
  target: 100,
  hasReached: false
})



onMounted(() => {
  console.log(scrollViewRef.value, 123)
  useEventListener(document, 'scroll', (e) => {
    e.preventDefault()
    console.log('eee')
    if (!d.hasReached) {
    }
  })
})
</script>

<template>
  <div class="demo-scroll" ref="scrollViewRef">
    <!-- -->
    demo-scroll
  </div>
</template>

<style lang="postcss">
.demo-scroll {
  @apply;
}
</style>
