<template>
  <div class="values">
    <div class="mt-32 title text-center text-white">
      <p class="text-6xl text-red-600 font-semibold">Our Stances</p>
      <p class="mt-1 text-sm text-white">Where do we stand on particular issues?</p>
    </div>

    <div class="values-list mt-32 w-full flex flex-wrap justify-center">
      <div 
        v-for="stance in stances"
        :key="stance.slug"
        class="stance bg-gray-500 m-4 md:m-8 px-4 py-2 w-64 h-32 shadow-xl text-white w-1/2 lg:w-1/3"
      >
        <NuxtLink :to="{ name: 'stances-slug', params: { slug: stance.slug } }">
          <div class="flex justify-center h-full items-center">
            <fa :icon="[stance.iconType, stance.icon]" class="flex-start text-4xl text-red-600 w-32"/>
            <p class="text-center text-2xl font-semibold pl-4 flex-end w-64">{{ stance.title }}</p>
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

<style lang="sass" scoped>

.stance
  background: #212121
  animation: grow-back 0.3s forwards

.stance:hover
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
