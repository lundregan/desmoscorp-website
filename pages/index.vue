<template>
  <div class="home h-screen w-full">
    <div class="intro relative h-full">
      <img
        src="~/assets/images/bg-arcade.jpg"
        alt=""
        class="intro-image w-full h-full opacity-75 shadow-md"
      />
      <div class="cent">
        <h1 class="text-6xl font-semibold text-red-600">Desmos Corporation</h1>
        <h2 class="text-xl text-white">A Mock Project by <a href="http://www.lundregan.com" class="text-blue-600">Ethan Lundregan</a></h2>
        <nuxt-link to="/games"
          ><button
            class="view-games bg-red-600 text-white p-8 shadow-xl mt-32 grow font-bold font-xl"
          >
            View Out Games
          </button></nuxt-link
        >
      </div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style lang="sass">
.intro, .test
  position: relative
  text-align: center

.intro-image, .test-image
  filter: sepia(50%), contrast(180%)
  object-fit: cover
  object-position: bottom

.cent
  position: absolute
  top: 50%
  left: 50%
  transform: translate(-50%, -50%)

.view-games
  animation: grow-back 0.2s forwards

.view-games:hover
  animation: grow 0.1s forwards

@keyframes grow
  from
    transform: scale(1.0)
  to
    transform: scale(1.05)

@keyframes grow-back
  from
    transform: scale(1.05)
  to
    transform: scale(1)    
</style>
