<template>
  <div class="flex justify-center text-white">
      <div class="game w-1/2 mt-8">
        <img :src="game.img" alt="" class="pb-4">
        <nuxt-content :document="game" class="" />
      </div>
  </div>
</template>

<script>
export default {
    async asyncData({ $content, params }) {
      const game = await $content('games', params.slug).fetch()

      return { game }
    }
  }
</script>

<style lang="sass" scoped>
@import url(http://fonts.googleapis.com/css?family=Open+Sans+Condensed:300,300italic,700)
@import url(http://fonts.googleapis.com/css?family=Arimo:700,700italic)

.game
  background: #212121
</style>