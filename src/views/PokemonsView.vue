<script setup>

// import axios from 'axios'
// import { ref } from 'vue';
import { RouterLink } from 'vue-router'

import { useGetData } from '@/composables/getData';

// const pokemons = ref([]);

const { data, getData, loading, errorData } = useGetData();

getData("https://pokeapi.co/api/v2/pokemon");






//sin composable o sin logica reutilizada
// const getData = async () => {
//     try {
//         const { data } = await axios.get("https://pokeapi.co/api/v2/pokemon");

//         pokemons.value = data.results;

//     } catch (error) {
//         console.log(error);

//     }
// }

// getData();

</script>



<template>
    <h1>Pokemons</h1>
    <p v-if="loading">Cargando información...</p>
    <div class="alert alert-danger mt-2" v-if="errorData">{{ errorData }}</div>
    <div v-if="data">
        <ul class="list-group">
            <li class="list-group-item" v-for="poke in data.results">
                <router-link :to="`/pokemons/${poke.name}`">{{ poke.name }}</router-link>
            </li>
        </ul>
        <div class="mt-2">
            <button :disabled="!data.previous" class="btn btn-warning me-2"
                @click="getData(data.previous)">Previous</button>
            <button :disabled="!data.next" class="btn btn-primary" @click="getData(data.next)">Next</button>
        </div>

    </div>
</template>