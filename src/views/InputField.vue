<template>
  <form class="SearchField">
    <input
        v-model="searchText"
        maxlength="50"
        class="SearchInput"
        v-on:input="changeInput(searchText.toLowerCase())"
        placeholder="Enter search word"
    >
  </form>
  <button
      type="button"
      class="Search__AddNewCountryBtn"
      v-on:click="addCountry(searchText)"
  >
    Add new country
  </button>
</template>

<script lang="ts">

import {defineComponent} from 'vue';

export default defineComponent({
  name: 'InputField',
  props: {
    changeInput: {
      type: Function,
    },
    addCountry: {
      type: Function,
    },
  },
  data: () => ({
    searchText: "",
  }),
});
</script>

<style scoped>
.SearchInput {
  width: 200px;
  height: 40px;
  margin-bottom: 20px;
  padding-left: 10px;
  color: #ffffff;
  background-color: plum;
  font-weight: bold;
  font-size: 1.03rem;
  border: none;
  border-radius: 15px;
}

.SearchInput::placeholder {
  color: #ffffff;
}

.Search__AddNewCountryBtn {
  padding: 10px 10px;
  font-weight: bold;
  background-color: white;
  color: dodgerblue;
  border: 1px solid dodgerblue;
  border-radius: 15px;
  margin-bottom: 25px;
}

.Search__AddNewCountryBtn:hover {
  background-color: #fffafa;

}
</style>



