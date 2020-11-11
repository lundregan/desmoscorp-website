<template>
<div class="w-full px-8 py-6 text-white">
  <p class="text-center">Want to see where we stand on other topics?</p>
  <div class="flex justify-between">
    <NuxtLink
      v-if="prev"
      :to="{ name: 'stances-slug', params: { slug: prev.slug } }"
      class="text-primary font-bold hover:underline  hover:text-red-600"
    >
      {{ prev.title }}
    </NuxtLink>
    <span v-else>&nbsp;</span>
    <NuxtLink
      v-if="next"
      :to="{ name: 'stances-slug', params: { slug: next.slug } }"
      class="font-bold hover:underline hover:text-red-600"
    >
      {{ next.title }}
    </NuxtLink>
    <span v-else>&nbsp;</span>
  </div>
</div>
</template>

<script>
  export default {
    props: {
      prev: {
        type: Object,
        default: () => null
      },
      next: {
        type: Object,
        default: () => null
      }
    }
  }
</script>

<style>
</style>
