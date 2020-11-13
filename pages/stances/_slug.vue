<template>
  <div class="flex justify-center">
    <article class="flex justify-center my-4 mx-2 sm:w-1/2 p-6 h-full  text-white shadow-xl mt-32">
    <div class="flex-col">
      <StancePrevNext :prev="prev" :next="next" class="mb-16 other-stances-links"/>

      <div class="self-center text-center">
        <fa :icon="[stance.iconType, stance.icon]" class="text-6xl text-red-600"/>
      </div>

      <nuxt-content :document="stance" class="" />
    </div>
  </article>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const stance = await $content('stances', params.slug).fetch()

    const [prev, next] = await $content('stances')
      .only(['title', 'slug'])
      .sortBy('createdAt', 'asc')
      .surround(params.slug)
      .fetch()

    return {
      stance,
      prev,
      next
    }
  },
};
</script>

<style lang="sass">
@import url(http://fonts.googleapis.com/css?family=Open+Sans+Condensed:300,300italic,700)
@import url(http://fonts.googleapis.com/css?family=Arimo:700,700italic)

article
  background: #212121

.other-stances-links
  border-bottom: 1px solid #313131

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
    color: #e53e3e

  h1, h2, h3
    margin-bottom: 1.15rem
    padding-bottom: .5rem
    text-align: center
  
  h1
    margin-top: 0
    border-bottom: 2px solid #e53e3e
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