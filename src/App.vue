<script setup>
// Components
import SearchBar from './components/SearchBar.vue'
</script>

<template>
  <header>
    <div class="wrapper">
      <SearchBar msg="Search Bar" />
    </div>
  </header>

</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}


</style>
