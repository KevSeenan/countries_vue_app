<template lang="html">
  <div>
    <ul>
      <list-item v-for="(country, index) in countries" :country="country" :key="index"></list-item>
    </ul>
  </div>
</template>

<script>
import ListItem from './ListItem.vue';

export default {
  name: 'countries-list',
  props: ['countries'],
  // data(){
  //   return {
  //     selectedCountry: null
  //   }
  },
  components: {
    "list-item": ListItem,
    "country-select": CountrySelect
  },
  // methods: {
  //   onChange(event){
  //     eventBus.$emit('country-selected', this.country);
  //   }
  }
}
</script>

<style lang="css" scoped>
</style>
