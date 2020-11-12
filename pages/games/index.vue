<template>
  <div class="p-16 flex justify-center flex-wrap flex-col">
    <p class="text-center text-6xl text-white border-b-2 border-white mx-64">
      Our Games
    </p>

    <NuxtLink
      :to="{ name: 'games-slug', params: { slug: game.slug } }"
      class="flex w-1/2 self-center bg-gray-800 m-12"
      v-for="game in games"
      :key="game.slug"
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

<style>
</style>