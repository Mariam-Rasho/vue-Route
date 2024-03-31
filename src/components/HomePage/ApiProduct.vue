<script>
import productElement from './productElement.vue';
import listFilterProduct from './listFilterProduct.vue'
export default {
    components: {
      productElement,
      listFilterProduct
    }
    ,
    data() {
        return {
          products: [],
          currentCategory:"All products"
        }
    },
     created() {
        fetch('https://fakestoreapi.com/products/').then(response=>response.json()).then(data=>{
          data.forEach(element => {
          let words=element.description.split(" ")
        let wordArr=words.splice(0,60).join(" ")
        element.description=wordArr;
        let ratingElm=parseInt(element.rating.rate)
            element.rating.rate=ratingElm;
        if(ratingElm== 2){
          element.rating.rate+=  "_⭐⭐"
        }if(ratingElm== 3){
          element.rating.rate+=  "_⭐⭐⭐"
        }if(ratingElm== 4){
          element.rating.rate+=  "_⭐⭐⭐⭐"
        }if(ratingElm == 5){
          element.rating.rate+=  "_⭐⭐⭐⭐⭐"
        }if(ratingElm == 1)
        {
          element.rating.rate+= "_⭐"
        }
        })
   this.products=data
      })},
  methods: {
    updateCurrentCategory(NewCategory) {
    this.currentCategory = NewCategory
}
  },

computed: {
filteredArray() {
  if(this.currentCategory=="All products"){
    return this.products;
  }
    return this.products.filter(a => a.category == this.currentCategory)
}
},
}
</script>

<template>
  <link rel="stylesheet"
  href="https://use.fontawesome.com/releases/v5.2.0/css/all.css"
  integrity="sha384-hWVjflwFxL6sNzntih27bfxkr27PmbbK/iSvJ+a4+0owXq79v+lsFkW54bOGbiDQ"
  crossorigin="anonymous">
  <link
      href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;500;600&display=swap"
      rel="stylesheet"
    />
  <section id="bg-products">
    <div class="header">
    <h1 class="titleProd">Products</h1>
    </div>
      <div>
        <listFilterProduct :prodArray="products"
        v-model="currentCategory">
        </listFilterProduct>
      </div>
      <div class="grid-container">
    <!-- Column 1-->
<productElement v-for="product in filteredArray" :key="product.id">
<template #source><img class="imagePro" :src="product.image" /></template>
<template #fullName>{{product.title}}</template>
<template #category>{{product.category}}</template>
<template #rate>{{product.rating.rate}}</template>
<template #count>{{product.rating.count}}</template>
<template #price> {{product.price}} $</template>
<template #description>{{product.description}}</template>
</productElement>
        </div>
    </section>
</template>

<style scoped>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  font-family: "Poppins", sans-serif;
  transition: 500ms;
}

#bg-products {
  width: 100%;
  height: 100%;
  background-image: url(../../assets/shopping.jpg);
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
  padding-top: 90px;
}
.grid-container{
display: grid;
grid-template-columns: repeat(2, 1fr);
gap: 50px 0;
place-items: center;
padding: 10px 50px;
}

.header {
  background: transparent;
  padding: 0.5rem 1rem;
  background-image: linear-gradient(10deg,  hsl(288, 39%, 82%), hsl(227, 44%, 83%)),
    linear-gradient(90deg, hsl(288, 54%, 80%), hsl(227, 44%, 83%));
  background-clip: padding-box, border-box;
  background-origin: border-box;
  border: 5px solid transparent;
  border-radius: 74px 10px 74px 10px;
  width: 500px;
  margin: 0px auto;
}

.titleProd {
  text-align: center;
  background-image: linear-gradient(
    70deg,
    hsl(289, 78%, 26%),
    hsl(294, 43%, 33%),
    hsl(311, 46%, 31%)
  );
  background-clip: text;
  -webkit-background-clip: text;
  color: transparent;
  font-weight: 600;
  font-size: 3rem;
  line-height: 3rem;
  text-shadow: 3px 10px 7px rgba(195, 110, 255, 0.46);
}

</style>