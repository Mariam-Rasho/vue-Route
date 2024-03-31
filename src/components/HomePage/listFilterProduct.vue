<template>
    <ul id="buttons">
        <li class="btn"> <button @click="$emit('update:modelValue', category)"
          v-for="category in categories" :key="category">
          {{ category }}
         </button>
        </li>
    </ul>
</template>

<script>
export default{
    props: {
        prodArray: {
      type: Array
    }, modelValue: {
      type: String
    }
  },
  computed: {
        categories() {
            return ["All products",...new Set(this.prodArray.map(t => t.category))]
        },
    }
}

</script>

<style>
#buttons{
    list-style: none;
    display: flex;
    justify-content: space-around;
    align-items: center;
    margin: 40px auto 20px;
}
#buttons li{
    background: transparent;
    background-image: linear-gradient(10deg,  hsl(288, 39%, 82%), hsl(227, 44%, 83%)),
      linear-gradient(90deg, hsl(288, 54%, 80%), hsl(227, 44%, 83%));
    background-clip: padding-box, border-box;
    background-origin: border-box;
    border: none;
    border-radius: 27px 10px;
}
button{
    background-color: rgb(178, 140, 208);
    border-radius: 10px;
    padding: 10px 25px;
    font-size: 25px;
    font-weight: 900;
    background-image:  linear-gradient(
        70deg,
        hsl(289, 78%, 26%),
        hsl(294, 62%, 59%),
        hsl(311, 50%, 24%)
      );
      background-clip: text;
      -webkit-background-clip: text;
      color: transparent;
    border: none;
    cursor: pointer;
}
</style>