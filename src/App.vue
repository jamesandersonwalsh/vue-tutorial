<!--
  ? All view components are Single File Components with responsibilities separated into script, template, and style
-->
<!-- * Logic Layer: -->
<script setup>
import { ref, reactive } from 'vue'
import socksGreenImage from './assets/images/socks_green.jpeg'
import socksBlueImage from './assets/images/socks_blue.jpeg'

const product = ref('Socks')
const image = ref(socksGreenImage)

const inStock = ref(true)
const details = ref(['50% cotton', '30% wool', '20% polyester'])
const variants = ref([
  { id: 2234, color: 'green', image: socksGreenImage },
  { id: 2235, color: 'blue', image: socksBlueImage }
])
const cart = reactive([])

const addToCart = (item) => {
  cart.push(item)
}
const updateImage = (variantImage) => {
  image.value = variantImage
}


</script>

<!--
  * View Layer:
    Template bindings support partial binding, any javascript expression can go in here.
-->
<template>
  <div class="nav-bar" />
  <div class="cart">Cart({{cart.length}})</div>
  <div class="product-display">
    <div class="product-container">
      <div class="product-image">
        <img v-bind:src="image" alt="green socks">
      </div>
      <div class="product-info">
        <h1>{{product}}</h1>
        <p v-if="inStock">In Stock</p>
        <p v-else>Out of Stock</p>
        <ul>
          <li v-for="detail in details">{{detail}}</li>
        </ul>
        <div
          v-for="variant in variants"
          :key="variant.id"
          @click="updateImage(variant.image)"
          class="color-circle"
          :style="{ backgroundColor: variant.color}"
          >
        </div>
        <button
          class="button"
          :class="{ disabledButton: !inStock }"
          @click="addToCart"
          :disabled="!inStock"
          >
          Add to Cart
        </button>
      </div>
    </div>
  </div>
</template>

<!-- * Style Layer: -->
<style scoped>
  .color-circle {
    cursor: pointer;
  }
</style>
