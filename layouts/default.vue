<template>
  <div class="layout h-screen">
    <Navbar />

    <Nuxt />
  </div>
</template>

<style lang="sass">
html
  font-family:'Source Sans Pro', Arial, sans-serif
  font-size: 16px
  word-spacing: 1px
  -ms-text-size-adjust: 100%
  -webkit-text-size-adjust: 100%
  -moz-osx-font-smoothing: grayscale
  -webkit-font-smoothing: antialiased
  box-sizing: border-box
  background: #313131

*
*::before
*::after
  box-sizing: border-box
  margin: 0

.button--green
  display: inline-block
  border-radius: 4px
  border: 1px solid #3b8070
  color: #3b8070
  text-decoration: none
  padding: 10px 30px

.button--green:hover
  color: #fff
  background-color: #3b8070

.button--grey
  display: inline-block
  border-radius: 4px
  border: 1px solid #35495e
  color: #35495e
  text-decoration: none
  padding: 10px 30px
  margin-left: 15px

.button--grey:hover
  color: #fff
  background-color: #35495e

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
