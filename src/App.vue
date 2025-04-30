<script setup>
import { ref } from 'vue';
let num = ref(0)
</script>

<template>
  <!-- NAVBAR -->
  <nav class="navbar navbar-expand-lg navbar-dark bg-primary">
  <div class="container-fluid">
      <router-link class="navbar-brand" to="/">
      <img src="https://cdn-icons-png.flaticon.com/512/188/188987.png" alt="Logo" width="30" height="24" class="d-inline-block align-text-top">
      
      </router-link>
    <router-link class="navbar-brand" to="/">Pokevite</router-link>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarNav">
      <ul class="navbar-nav">
        <li class="nav-item">
          <router-link class="nav-link" aria-current="page" to="/">Home</router-link>
        </li>
        <li class="nav-item">
          <router-link class="nav-link" to="/about">About</router-link>
        </li>
      </ul>
    </div>
  </div>
</nav>
<!-- CONTENT -->
 <div class="main">
  <!-- vaão ser renderizadas as rotas do projeto -->
  <router-view></router-view>
 </div>

 <!-- FOOTER -->
  <footer class="bg-primary text-light">
    <div>Design in {{ new Date().getFullYear() }} | Udemy Student | v 1.0.1</div>
  </footer>
</template>

<style>
body{
  height: 100vh;
  background: #3222c3;
  background: linear-gradient(178deg,rgba(50, 34, 195, 1) 7%, rgba(45, 253, 239, 1) 100%);
}

footer{
  position: fixed;
  bottom: 0;

  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 40px;
}

</style>
