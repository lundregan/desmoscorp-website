<template>
  <div class="flex justify-center">
    <article class="flex justify-center my-4 mx-2 sm:w-1/2 p-6 h-full  text-white shadow-xl mt-32">
    <div class="flex-col">
      <StancePrevNext :prev="prev" :next="next" class="mb-16 other-stances-links"/>

      <div class="self-center text-center">
        <fa :icon="[stance.iconType, stance.icon]" class="text-6xl text-red-600"/>
      </div>

      <nuxt-content :document="stance" class="" />
    </div>
  </article>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const stance = await $content('stances', params.slug).fetch()

    const [prev, next] = await $content('stances')
      .only(['title', 'slug'])
      .sortBy('createdAt', 'asc')
      .surround(params.slug)
      .fetch()

    return {
      stance,
      prev,
      next
    }
  },
};
</script>

<style lang="sass" scoped>
@import url(http://fonts.googleapis.com/css?family=Open+Sans+Condensed:300,300italic,700)
@import url(http://fonts.googleapis.com/css?family=Arimo:700,700italic)

article
  background: #212121

.other-stances-links
  border-bottom: 1px solid #313131
</style>