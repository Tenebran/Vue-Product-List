<script>
import axios from 'axios'

export default {
  data() {
    return {
      products: []
    }
  },

  mounted() {
    axios.get('https://fakestoreapi.com/products').then((res) => (this.products = res.data))
  }
}
</script>

<script setup>
import MyHeader from './components/MyHeader.vue'
import ProductItem from './components/ProductItem.vue'
</script>

<template>
  <my-header></my-header>
  <section class="wrapper__item">
    <ul class="products">
      <product-item
        v-for="list in products"
        :key="list.id"
        :title="list.title"
        :description="list.description"
        :image="list.image"
        :price="list.price"
        :count="list.rating.count"
        :rating="list.rating.rate"
      ></product-item>
    </ul>
  </section>
</template>

<style scoped lang="scss">
.products {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-evenly;
  margin-top: 120px;
}
</style>
