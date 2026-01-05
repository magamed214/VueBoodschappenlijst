<script setup>
import { reactive, computed } from 'vue';

const products = reactive([
  {food: 'Rijst', number: 1, price: 1.00},
  {food: 'Broccoli', number: 2, price: 0.99},
  {food: 'Koekjes', number: 4, price: 1.20},
  {food: 'Noten', number: 0, price: 2.99}
])

const totalPrice = computed(() => {
  return products.reduce((total, product) => product.number * product.price + total, 0);
});
</script>

<template>
  <div class="shopping-list">
    <h2>Boodschappenlijst</h2>
    <ul>
      <li v-for="product in products" :key="product.food">
        <span class="product-name">{{ product.food }}:</span>
        <input type="number" v-model.number="product.number" min="0" />x
        <span class="subtotal">{{ (product.number * product.price).toFixed(2) }} EUR</span>
      </li>
    </ul>
    <div class="total">
      <strong>Totaal: {{ totalPrice.toFixed(2) }} EUR</strong>
    </div>
  </div>
</template>



