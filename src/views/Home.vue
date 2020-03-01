<template>
  <div class="home">
    <div class="container mx-auto">
      <h1 class="py-12 text-6xl text-green-900">
        Times
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
