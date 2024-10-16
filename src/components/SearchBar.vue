<script setup>
// Vue
import { ref } from 'vue'

// Data 
import data from "../dummyData.json"

// Components
import Data from "./Data.vue"

defineProps({
  msg: {
    type: String,
    required: true
  }
})

const text = ref("")
</script>

<template>
  <div class="searchBarWrapper">
    <h1 class="green">{{ msg }}</h1>
    <input
      class="searchBar"
      :value="text"
      @input="event => text = event.target.value"
      placeholder="Type here..."
    >
    <div v-for="info in data">
      <Data :info="info"/>
    </div>
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

.searchBar {
  width: 420px;
  height: 45px;
  border-radius: 10px;
  padding: 10px;
  margin: auto;
  margin-bottom: 25px;
}
</style>
