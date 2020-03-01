<template>
  <div id="app">
    <home />
  </div>
</template>

<script>
  import Home from './views/Home.vue'

  export default {
    name: 'App',
    components: {
      Home
    }
  }
</script>

<style lang="stylus">
  @import "~tailwindcss/dist/tailwind.css"

  #app
    font-family Avenir, Helvetica, Arial, sans-serif
    text-align center
</style>
