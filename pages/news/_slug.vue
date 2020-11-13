<template>
  <div class="flex justify-center">
    <div class="news text-white mt-32 py-16 px-32 shadow-md">
      <nuxt-content :document="article"/>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const article = await $content("news", params.slug).fetch();

    return { article };
  },
};
</script>

<style lang="sass">
@import url(http://fonts.googleapis.com/css?family=Open+Sans+Condensed:300,300italic,700)
@import url(http://fonts.googleapis.com/css?family=Arimo:700,700italic)

.news
  background: #212121
</style>