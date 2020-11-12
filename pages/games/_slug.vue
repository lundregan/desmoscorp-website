<template>
  <div class="flex justify-center text-white">
      <div class="w-1/2 mt-8">
        <img :src="game.img" alt="" class="m-4">
        <nuxt-content :document="game" class="" />
      </div>
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

<style lang="sass">
@import url(http://fonts.googleapis.com/css?family=Open+Sans+Condensed:300,300italic,700)
@import url(http://fonts.googleapis.com/css?family=Arimo:700,700italic)

.nuxt-content
  line-height: 1.85
  font-family: roboto, sans-serif
  font-weight: 300
  margin: 0 auto
  max-width: 48rem
  line-height: 1.45
  padding: .25rem
  
  p
    font-size: 1rem
    margin-bottom: 1.3rem
  
  a
    color: #e53e3e

  a:hover, a:focus, a:active
    color: #2980b9

  h1, h2, h3, h4
    margin: 2.5rem 0 .5rem
    font-weight: inherit
    line-height: 1.42
    font-family: Arimo, Helvetica, sans-serif

  h1, h2, h3
    margin-bottom: 1.15rem
    padding-bottom: .5rem
    text-align: center
  
  h1
    margin-top: 0
    border-bottom: 2px solid #fafafa
    font-size: 3.998rem
  
  h2
    font-size: 2.827rem
  
  h3  
    font-size: 1.999rem
  
  h4
    font-size: 1.414rem
  
  h5
    font-size: 1.121rem
  
  h6
    font-size: .88rem
  
  small
    font-size: .707em
  
  img, canvas, iframe, video, svg, select, textarea
    max-width: 100%

  blockquote
    padding: 1rem
  
  pre, code
    background-color: #fafafa

</style>