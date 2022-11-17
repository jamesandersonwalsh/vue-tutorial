<!--
  ? All view components are Single File Components with responsibilities separated into script, template, and style
-->
<!-- * Logic Layer: -->
<script setup>
import { ref } from 'vue';
const useChangeWithDelay = (state, newVal, delay) => {
  setTimeout(() => {
    state.value = newVal
  }, delay)
}
const product = ref('Socks') // Vue equivalent of useState in React.

useChangeWithDelay(product, 'New Socks', 1000)
</script>

<!-- * View Layer: -->
<template>
  <!-- Supports partial binding, any javascript expression can go in here. -->
  <h1>{{ product }}</h1>
</template>

<!-- * Style Layer: -->
<style scoped>
</style>
