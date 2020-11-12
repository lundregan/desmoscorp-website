<template>
  <div class="flex flex-col">
    <NuxtLink
      :to="{ name: 'news-slug', params: { slug: article.slug } }"
      class="flex w-1/4 self-center bg-gray-800 m-12 p-8 text-center rounded-xl"
      v-for="article in news"
      :key="article.slug"
    >
      <div class="pl-4 text-white w-full">
        <p class="text-4xl text-red-600 font-semibold">{{ article.title }}</p>
        <p class="mt-4">{{ article.description }}</p>
      </div>
    </NuxtLink>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const news = await $content("news", params.slug)
      .only(["title", "description", "slug"])
      .sortBy("createdAt", "asc")
      .fetch();

    return {
      news,
    };
  },
};
</script>

<style>
</style>