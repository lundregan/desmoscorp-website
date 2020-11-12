<template>
  <div>
      <p>{{game.name}}</p>
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

<style>

</style>