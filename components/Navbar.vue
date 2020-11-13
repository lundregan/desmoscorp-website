<template>
  <div class="navbar shadow-md w-full flex justify-between align-center text-white px-4 pb-2 pt-4">
    <div class="brand">
      <p class="font-semibold text-2xl text-red-600">DESMOS CORP</p>
      <p class="text-xs pl-5">No Expense Innovation</p>
    </div>
    <div class="corp-links w-1/2 lg:w-1/5 flex flex-col sm:flex-row justify-around text-right">
      <div
        v-for="link in links"
        :key="link.id"
        class=""
      >
        <nuxt-link 
          :to="link.link"
          class="text-xl"
        >
          <p class="grows">
            {{link.name}}
          </p>
        </nuxt-link>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      links: [
        {
          link: '/',
          name: 'Home'
        },
        {
          link: '/stances',
          name: 'Stances'
        },
        {
          link: '/games',
          name: 'Games'
        },
        {
          link: '/news',
          name: 'News'
        }
      ]
    }
  }
}
</script>

<style lang="sass">
.navbar
  background: #212121

.grows
  animation: grow-back 0.2s forwards linear, link-deselected 2s forwards

.grows:hover
  animation: grow 0.1s forwards ease-in-out, link-selected 1s forwards

@keyframes grow-back
  from
    transform: scale(1.25)
  to
    transform: scale(1)

@keyframes grow
  from
    transform: scale(1)
  to
    transform: scale(1.25)

@keyframes link-selected
  from
    color: white
  to
    color: #c53030

@keyframes link-deselected
  from
    color: #c53030
  to
    color: white
</style>
