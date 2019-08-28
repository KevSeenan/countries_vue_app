<template lang="html">
  <div>
      <label for="country-select">Select A Country:</label>
      <select v-model="country" v-on:change="handleChange()">
        <option disabled value="">Select A Country</option>
        <option v-for="(country, index) in countries" :value="country" :key="index">{{country.name}}</option>
      </select>
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
    }
  }
}
</script>

<style lang="css" scoped>
</style>
