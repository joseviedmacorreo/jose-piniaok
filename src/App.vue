<script setup>
import { RouterLink, RouterView } from 'vue-router'

</script>

<template>
  <nav class="navbar bg-dark navbar-dark">
    <div class="container">
      <router-link class="navbar-brand" to="/">
        <img src="@/assets/logo.svg" alt="" width="30" height="24">
        PokeAPI</router-link>

        <router-link to="/" class="btn btn-outline-primary">Home</router-link>
        <router-link to="/pokemons" class="btn btn-outline-primary">Pokemons</router-link>
        <router-link to="/favoritos" class="btn btn-outline-primary">Favoritos</router-link>
    </div>
  </nav>

  <div class="container text-center">
    <RouterView />
  </div>



</template>

