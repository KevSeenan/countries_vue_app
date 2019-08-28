<template lang="html">
  <div>
    <label for="country-select">Select A Country:</label>
    <select v-model="country" v-on:change="handleChange">
      <option disabled value="">Select A Country</option>
      <option v-for="(country, index) in countries" :value="country" :key="index">{{country.name}}</option>
    </select>

    <label for="country-select">Search Countries:</label>
    <input type="search" id="site-search">
    <datalist>
      <option v-for="(country, index) in countries" :value="country" :key="index">{{country.name}}></option>
    </datalist>

    <button v-model="country" v-on:click="handleClick">Search</button>

  </div>
</select>
</template>

<script>
import {eventBus} from '../main.js';

export default {
  name: 'country-select',
  data(){
    return {
      country: null
    }
  },
  props: ['countries'],
  methods: {
    handleChange(){
      eventBus.$emit('country-selected', this.country);
    },
    handleClick(){
      eventBus.$emit('country-selected', this.country);
      console.log('Hello');
    }
  }
}
</script>

<style lang="css" scoped>
</style>
