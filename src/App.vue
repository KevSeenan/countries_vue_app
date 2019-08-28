<template lang="html">
  <div>
    <link href="https://fonts.googleapis.com/css?family=Gayathri&display=swap" rel="stylesheet">
    <h1>Countries App</h1>
    <div class="main-container">
      <country-select :countries='countries'></country-select>
      <country-detail v-if="selectedCountry" :country="selectedCountry"></country-detail>
    </div>
  </div>
</template>

<script>

import CountryDetail from './components/CountryDetail.vue';
import CountrySelect from './components/CountrySelect.vue';
import {eventBus} from './main.js';

export default {
  name: 'app',
  data(){
    return {
      countries: [],
      selectedCountry: null
    };
  },
  mounted(){
    fetch('https://restcountries.eu/rest/v2/all')
    .then(res => res.json())
    .then(countries => this.countries = countries)

    eventBus.$on('country-selected', (country) => {
      this.selectedCountry = country;
    })
  },
  components: {
    "country-detail": CountryDetail,
    "country-select": CountrySelect
  }
}
</script>

<style>

  body {
    background-color: #DEB887;
    background-position: top;
    background-repeat: no-repeat;
    font-family: 'Gayathri', sans-serif;
    text-align: justify;
    color: #000000;
  }

  li {
    list-style: none;
  }

  h1, h3 {
    text-decoration: underline;
  }

  .main-container {
    display: block;
    justify-content: space-between;
  }

</style>
