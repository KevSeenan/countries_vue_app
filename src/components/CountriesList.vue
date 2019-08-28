<template lang="html">
  <div>
    <!-- <label for="country-select">Select A Country:</label>
    <select id="country-select" v-model="selectedCountry">
      <option disabled value="">Select A Country</option>
      <list-item v-for="(country, index) in countries" :country="country" :key="index"></list-item>
    </select> -->

    <ul>
      <list-item v-for="(country, index) in countries" :country="country" :key="index"></list-item>
    </ul>
  </div>
</template>

<script>
import ListItem from './ListItem.vue';
import {eventBus} from '../main.js';

export default {
  name: 'countries-list',
  props: ['countries'],
  // data(){
  //   return {
  //     selectedCountry: null
  //   }
  // },
  components: {
    "list-item": ListItem
  },
  methods: {
    onChange(event){
      eventBus.$emit('country-selected', this.country);
    }
  }
}
</script>

<style lang="css" scoped>
</style>
