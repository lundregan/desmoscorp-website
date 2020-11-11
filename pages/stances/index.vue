<template>
  <div class="values">
    <div class="title text-center text-white">
      <p class="mt-4 text-6xl">Our Stances</p>
      <p class="mt-2 text-xl">Where do we stand on certain topics related to gaming. Do we agree with things like DRM and Lootboxes or not?</p>
    </div>

    <div class="values-list m-4 w-full flex flex-wrap justify-center">
      <div 
        v-for="stance in stances"
        :key="stance.slug"
        class="lg:w-1/4 bg-gray-500 m-4 md:m-8 px-4 py-2 w-64 h-32 rounded-xl shadow-md bg-blue-500 text-white"
      >
        <NuxtLink :to="{ name: 'stances-slug', params: { slug: stance.slug } }">
          <div class="flex h-full justify-center items-center">
            <fa :icon="[stance.iconType, stance.icon]" class="text-4xl"/>
            <p class="text-2xl font-semibold pl-4">{{ stance.title }}</p>
          </div>
        </NuxtLink>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    async asyncData({ $content, params }) {
      const stances = await $content('stances', params.slug)
        .only(['title', 'description', 'slug', 'icon', 'iconType'])
        .sortBy('createdAt', 'asc')
        .fetch()

      return {
        stances
      }
    }
  }
</script>

<style></style>
