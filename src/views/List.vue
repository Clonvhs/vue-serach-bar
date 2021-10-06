<template>
  <ul class="List">
    <li v-for="country in countriesList" :key="country" class="List__CountryItem">
      {{ capitalizeFirstLetter(country) }}
    </li>
  </ul>
</template>

<script lang="ts">

import {defineComponent} from 'vue';

export default defineComponent({
  name: 'List',
  props: {
    countriesList: {
      type: Array,
    },
  },
  data: (props) => ({
    countries: props.countriesList,
  }),
  methods: {
    capitalizeFirstLetter(string:string) {
  return string.charAt(0).toUpperCase() + string.slice(1);
}
  }
});
</script>

<style scoped>
.List {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 0;
  padding: 0;
  list-style-type: none;
}
.List__CountryItem {
  width: 35%;
  margin-bottom: 10px;
  background-color: gainsboro;
  border-radius: 15px
}
</style>
