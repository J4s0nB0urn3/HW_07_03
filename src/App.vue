<template lang="html">
  <div>
    <h1 style="margin-left: 50px;">Countries</h1>
    <div class="container">
      <!--test-->
      <!-- <country-select :countries='countries'></country-select> -->
      <countries-list :countries='countries'></countries-list>
      <country-detail :country='selectedCountry'></country-detail>

    </div>
  </div>
</template>

<script>

import CountryDetail from './components/CountryDetail.vue'
import {eventBus} from './main.js'
import CountriesList from './components/CountriesList.vue'
// test
// import CountrySelect from './components/CountrySelect.vue'
//
export default {
  name: 'app',
  data() {
    return {
      countries: [],
      selectedCountry: null
    };
  },
  mounted() {
    fetch("https://restcountries.eu/rest/v2/all")
    .then(response => response.json())
    .then(countries => this.countries = countries)

    eventBus.$on('country-selected', (country) => {
      this.selectedCountry = country;
    })
  },
  components: {
    "countries-list": CountriesList,
    "country-detail": CountryDetail,

    // "country-select": CountrySelect
  }
}
</script>

<style lang="css" scoped>
  .container {
    display: flex;
    justify-content: space-between;
    margin-right: 200px;
    margin-left: 50px;
  }
</style>
