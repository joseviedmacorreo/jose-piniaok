<script setup>

// import axios from 'axios';
import { useRoute, useRouter } from 'vue-router';
// import {ref} from 'vue';

import { useGetData } from '@/composables/getData'

import {useFavoritosStore} from '@/store/favoritos';

const route = useRoute();
const router = useRouter();

const useFavoritos = useFavoritosStore();

const {add, findPoke} = useFavoritos;

// const poke = ref({});
const { data, getData, loading, errorData } = useGetData();

const back = () => {
    router.push('/pokemons')
}

// const getData = async () => {
//     try {
//         const {data} = await axios.get(`https://pokeapi.co/api/v2/pokemon/${route.params.name}`);
//         console.log(data);
//         poke.value = data;

//     } catch (error) {
//         console.log(error);
//         poke.value = null;        
//     }
// }

// getData();
getData(`https://pokeapi.co/api/v2/pokemon/${route.params.name}`);



</script>


<template>
    <p v-if="loading">Cargando información...</p>
    <div class="alert alert-danger mt-2" v-if="errorData">No existe el Pokemon</div>
    <div v-if="data">
        <img :src="data.sprites?.front_default" alt="">
        <h1>Poke name: {{ $route.params.name }}</h1>
        <button :disabled="findPoke(data.name)" class="btn btn-primary mb-2" @click="add(data)">Agregar Favorito</button>
    </div>
    <!-- <h1 v-else>No existe el Pokemon</h1> -->
    <button @click="back" class="btn btn-outline-primary">Volver</button>
</template>