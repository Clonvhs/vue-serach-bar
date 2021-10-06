<template>
  <div class="Search__FormWrapper">
    <InputField
        v-bind:changeInput="handleInputChange"
        v-bind:addCountry="handleAddNewCountry"
    />
  </div>

  <List v-bind:countriesList="countriesList"/>
</template>

<script lang="ts">

import {defineComponent} from 'vue';
import List from "@/views/List.vue";
import store from "@/store";
import InputField from "@/views/InputField.vue"; // @ is an alias to /src

export default defineComponent({
  name: 'Search',
  components: {InputField, List},
  data: () => ({
    countriesList: [...store.state.countryList],
  }),
  methods: {
    handleInputChange(searchText: string) {
      this.countriesList = [...store.state.countryList].filter(country => country.includes(searchText))
    },
    handleAddNewCountry(countryName: string) {
      if(!this.countriesList.includes(countryName) && countryName.length > 0) {
        this.countriesList = [...this.countriesList, countryName]
            .sort((firstVal, secondVal) => firstVal.localeCompare(secondVal))
      }
      }
  }
});
</script>

<style>
</style>
