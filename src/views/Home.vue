<template>
  <div class="home">
    <div class="container mx-auto">
      <h1 class="pt-20 pb-12 text-4xl text-green-900">
        Gabe's Swim Times
      </h1>
      <times-table />
    </div>
  </div>
</template>

<script>
  import TimesTable from '../components/TimesTable'

  export default {
    name: 'Home',
    components: {
      TimesTable
    }
  }
</script>
