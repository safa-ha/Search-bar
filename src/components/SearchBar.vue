<script setup>
// Vue
import { ref, computed } from 'vue'
// Data 
import data from "../dummyData.json"

//Props
defineProps({
  msg: {
    type: String,
    required: true
  }
})

// Data
const text = ref("")

// Computed
const filteredData =computed(() => {
  const searchedText = text.value.toLowerCase()

  return data.filter(el => 
    el.name.toLowerCase().includes(searchedText) ||
    el.address.toLowerCase().includes(searchedText) ||
    el.postalZip.toLowerCase().includes(searchedText) ||
    el.region.toLowerCase().includes(searchedText) ||
    el.email.toLowerCase().includes(searchedText)
  )
})

// Functions
const highlightedText = (text, element) => {
  if (!text.length) return element
  const regex = new RegExp(`${text}`, "gi")
  let highlightedData = ""
  highlightedData = element.replace(
    regex,
    `<mark class="highlightText">${text}</mark>`
  )
  return highlightedData
}
</script>

<template>
  <div class="searchBarWrapper">
    <h1 class="green">{{ msg }}</h1>
    <input
      class="searchBar"
      :value="text"
      @input="event => text = event.target.value"
      placeholder="Search..."
    >
    <div v-if="filteredData" v-for="info in filteredData">
      <div id="box">
        <span v-html="highlightedText(text, info.name)"></span> <br />
        <span v-html="highlightedText(text, `${info.address}, ${info.region}, ${info.postalZip}`)"></span><br />
        <span v-html="highlightedText(text, info.phone)"></span> <br />
        <span v-html="highlightedText(text, info.email)"></span> <br />
      </div> <br />
    </div>
    <div v-else>No data found...</div>
  </div>
</template>

<style scoped>
.searchBarWrapper {
  min-height: 100vh;
}

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

.highlightText {
  background: yellow !important;
  color: black;
}
</style>
