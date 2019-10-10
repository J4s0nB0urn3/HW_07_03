<template lang="html">

  <!-- <option @change="handleClick($event)">{{country.name}}</option> -->

  <li v-on:click="handleClick">{{country.name}}</li>
</template>

<script>

import {eventBus} from '../main.js'

export default {
  name: 'list-component',
  props: ['country'],
  methods: {
    handleClick(event) {
      eventBus.$emit('country-selected', this.country)
    }
  }
}
</script>

<style lang="css" scoped>
li {
  list-style: none;
}

li:hover {
  border: 2px solid black;
  cursor: pointer;
}
</style>
