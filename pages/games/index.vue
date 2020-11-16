<template>
  <div class="flex justify-center flex-wrap flex-col my-32">
    <p class="text-center text-6xl mx-64 text-red-600 mb-16 font-semibold">
      Our Games
    </p>

    <NuxtLink
      :to="{ name: 'games-slug', params: { slug: game.slug } }"
      v-for="game in games"
      :key="game.slug"
      class="game-link-div flex w-1/2 self-center mt-16 shadow-md"
    >
      <div class="h-auto w-64">
        <img :src="game.img" alt="" />
      </div>
      <div class="pl-4 text-white">
        <p class="text-4xl text-red-600 font-semibold">{{ game.name }}</p>
        <p class="mt-4">{{ game.description }}</p>
        <p class="mt-6">{{ game.released }}</p>
      </div>
    </NuxtLink>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const games = await $content("games", params.slug)
      .only(["name", "img", "description", "released", "slug"])
      .sortBy("createdAt", "asc")
      .fetch();

    return {
      games,
    };
  },
};
</script>

<style lang="sass" scoped>
.game-link-div
  background: #212121
  animation: grow-back 0.5s forwards

.game-link-div:hover
  animation: grow 0.5s forwards

@keyframes grow
  from
    transform: scale(1)
  to
    transform: scale(1.11)

@keyframes grow-back
  from
    transform: scale(1.11)
  to
    transform: scale(1)
</style>