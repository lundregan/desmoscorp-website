<template>
  <div class="flex flex-col">
    <p class="text-center text-red-600 text-6xl my-32">NEWS</p>

    <NuxtLink
      :to="{ name: 'news-slug', params: { slug: article.slug } }"
      class="news-item flex w-1/4 self-center m-12 p-8 text-center shadow-md"
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

<style lang="sass" scoped>
.news-item
  background: #212121
  animation: grow-back 0.6s

.news-item:hover
  animation: grow 0.5s forwards

@keyframes grow
  from
    transform: scale(1)
  to
    transform: scale(1.32)

@keyframes grow-back
  from
    transform: scale(1.32)
  to
    transform: scale(1)
</style>