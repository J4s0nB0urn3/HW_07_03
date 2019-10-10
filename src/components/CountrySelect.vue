<template lang="html">
  <div>
    <select>
     <list-component v-for="(country, index) in countries" :country="country" :key="index">{{country.name}}</list-component>
     </select>

  </div>
</template>

<script>

import ListComponent from './ListComponent.vue'

export default {
  name: 'country-select',
  props: ['countries'],
  components: {
    "list-component": ListComponent
  }
}
</script>

<style lang="css" scoped>
</style>
