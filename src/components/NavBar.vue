<script>
import {RouterLink} from 'vue-router';

export default{
    components:{
        RouterLink
    }
}
</script>
<template>
    <nav class="navbar navbar-expand-sm fixed-top  navbar-light py-1 px-5 fw-bolder d-flex align-items-center">
        <div class="container-fluid">


      <a class="navbar-brand fs-2 text-dark" href="#">
        <img alt="Vue logo" class="me-2" src="@/assets/logo.svg" height="40" width="30"/><span>Vue Router</span></a>
          <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#mynavbar">
            <span class="navbar-toggler-icon"></span>
          </button>

        </div>
        <div class="collapse navbar-collapse d-flex me-3 " id="mynavbar">
            <ul class="navbar-nav me-auto ">
              <li class="nav-item ms-3 fs-4 link-opacity-75-hover ">
                <RouterLink to="/" class="unLine">Products</RouterLink>
              </li>
              <li class="nav-item ms-3 fs-4 link-opacity-75-hover">
                <RouterLink to="/about" class="unLine">Todos</RouterLink>
              </li>
            </ul>
          </div>
      </nav>
</template>