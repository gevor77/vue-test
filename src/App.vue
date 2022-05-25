<template>
  <div class="container">
    <div>
      <AddingNewProduct @add-price="addProduct"/>
    </div>
    <div>
      <AllProducts v-bind:products="products" @remove-product="removeProduct" />
    </div>
  </div>
</template>

<script>
import AllProducts from './components/AllProducts.vue'
import AddingNewProduct from './components/AddingNewProduct.vue'
import db from '../db.json'
export default {
  name: 'App',
  data() {
    return {
      products: db
      // [
        // {
        //   id:1,
        //   title: 'Наименование товара',
        //   text:'Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк',
        //   img: "Rectangle31",
        //   price: 10000
        //  },
        //  {
        //   id:2, 
        //   title: 'Наименование товара',
        //   text:' hello-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк',
        //   img: "Rectangle31",
        //   price: 10000
        //  },
        //  {
        //   id:3, 
        //   title: 'Наименование товара',
        //   text:'Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк',
        //   img: "Rectangle31",
        //   price: 10000
        //  },
        //  {
        //   id:4, 
        //   title: 'Наименование товара',
        //   text:'Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк',
        //   img: "Rectangle31",
        //   price: 10000
        //  }
      // ]
    }
  },
  methods: {
    addProduct(product) {
      this.products.push(product)
      console.log(product)
    },
    removeProduct(id){
      this.products = this.products.filter(a => a.id !== id)
    }
  },
  components: {
    AllProducts,
    AddingNewProduct
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 0;
  padding: 30px 25px;
  background-color: #E5E5E5;
}
.container {
  display: flex;
}
</style>
