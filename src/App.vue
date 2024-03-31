<script>
import  {RouterView}  from 'vue-router';
import FooterPage from './components/FooterPage.vue';
import NavBar from './components/NavBar.vue';
export default{
  components:{
    RouterView,
    FooterPage,
    NavBar
  }
}
</script>

<template>
  <NavBar/>
  <RouterView/>
  <FooterPage/>
</template>

<style>
nav{
  background: linear-gradient(30deg, rgba(52, 64, 57, 0.594) 0%,#221b3f8e 40%, rgba(103, 80, 108, 0.469) );
  -webkit-backdrop-filter: blur(10px);
  backdrop-filter: blur(10px);
}
.navbar-brand span
{
 color: rgb(0, 53, 35);
}
ul li .unLine{
  text-decoration: none;
  color: #221b3fd1;
}
ul li .unLine:hover{
  color: rgba(77, 57, 92, 0.982);
}
footer {
  text-align: center;
  padding: 10px;
  background: linear-gradient(30deg, rgba(52, 64, 57, 0.594) 0%,#221b3f8e 40%, rgba(103, 80, 108, 0.469) );
  color: white;
}
</style>