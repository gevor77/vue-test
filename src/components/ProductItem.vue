<template>
    <div class="product-item">
        <img src="../../public/Vector.png" class="vector" v-on:click="$emit('remove-product',product.id)"/>
        <div class="item-img">
            <img :src="getImgUrl(product.img)" v-bind:alt="product.img">
        </div>
        <div class="product-info">
            <h3>{{product.title}}</h3>
            <p>
                {{product.text}}
            </p>
            <p>{{product.price}} руб.</p>
        </div>
    </div>
</template>

<script>
export default {
  name: 'ProductItem',
  props: {
      product: {
          type: Object,
          required: true
      }
  },
  methods:  {
       getImgUrl(pet) {
        var images = require.context('../assets/', false, /\.png$/)
        return images('./' + pet + ".png")
    }
  }
   
}
</script>
<style>
  .product-item {
    width: 332px;
    height: 423px;
    text-align:left;
    background: #FFFEFB;
    box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02);
    border-radius: 4px;
    margin-left:10px;
    margin-top: 15px;
    position:relative;
  }
  .product-item .product-info p {
    height: 75px;
    overflow: hidden;
  }
  .product-item .product-info h3{
    height: 24px;
    overflow: hidden;
  }
  .product-item:hover .vector{
    display:block;
  }
  .product-info{
    padding:0 12px;
    cursor:pointer;
  }
  .vector{
    position: absolute;
    right: -6px;
    top: -6px;
    background: #FF8484;
    box-shadow: 0px 2px 4px rgb(0 0 0 / 10%);
    border-radius: 10px;
    padding: 12px;
    display:none;
  }
  .product-info h3 {
    font-family: 'Source Sans Pro';
    font-style: normal;
    font-weight: 600;
    font-size: 20px;
    line-height: 25px;
    color: #3F3F3F;
  }
</style>