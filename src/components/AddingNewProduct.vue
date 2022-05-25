<template>
    <div class="new-product">
        <form @submit.prevent="onSubmit">
            <label for="productName">Наименование товара<span class="required">*</span></label>
            <input v-model="title" class="form-control" id="productName" placeholder="Введите наименование товара" required/>
            <label for="text">Описание товара</label>
            <textarea placeholder="Введите описание товара" v-model="text" id="text"></textarea>
            <label for="img">Ссылка на изображение товара<span class="required">*</span></label>
            <input placeholder="Введите ссылку" type="text" v-model="img" class="form-control" id="img" required/>
            <label for="price">Цена товара<span class="required">*</span></label>
            <input placeholder="Введите цену" type="text" v-model="price" class="form-control" id="price" required />
            <p><button  class="btn btn-primary">Добавить товар</button></p>
        </form>
    </div>
</template>

<script>
export default {
  name: 'AddingNewProduct',
  methods: {
    onSubmit () {
      if(this.title.trim() && this.img.trim()) {
          const newProduct = {
              id: Date.now(),
              title: this.title,
              text: this.text,
              img: this.img,
              price: this.price,
          }
          this.$emit('add-price', newProduct)
          this.title = ''
          this.text = ''
          this.img = ''
          this.price = ''
      }
    }
  },
  data () {
      return {
          title:'',
          text:'',
          imgLink:'',
          price:''
      }
  }
}
</script>

<style>
    .new-product{
        background-color:#fff;
        padding:25px;
        text-align:left;
        margin-top: 15px;
        position: sticky;
        top: 0;
    }
    label{
        font-family: 'Source Sans Pro';
        font-style: normal;
        font-weight: 400;
        font-size: 13px;
        line-height: 13px;
        letter-spacing: -0.02em;
        color: #49485E;
        text-align:left;
        margin:5px 0;
        padding:8px 0;
        display: block;
    }
    .required {
        color: red;
    }
    input,textarea{
        width: 284px;
        height: 36px;
        left: 56px;
        top: 124px;
        background: #FFFEFB;
        box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
        border-radius: 4px;
        border:none;
        padding-left:7px;
    }
    .btn{
        width: 284px;
        height: 36px;
        background: #EEEEEE;
        border-radius: 10px;
        border:none;
    }
</style>