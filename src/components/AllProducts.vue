<template>
    <div class="products">
      <ProductItem v-for="product of products" v-bind:key="product" v-bind:product="product" 
      v-on:remove-product="removeProduct" />
    </div>
</template>

<script>
import ProductItem from './ProductItem.vue'
// import AddingNewProductVue from './AddingNewProduct.vue'

export default {
  name: 'AllProducts',
  props: ['products'],
  components: {
    ProductItem,
    // AddingNewProductVue
  },
  methods:{
    removeProduct(id){
      this.$emit('remove-product',id)
    }
  }
}
</script>

<style>
  .products{
    display:flex;
    flex-wrap: wrap;
  }
</style>