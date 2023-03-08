<template>
    <div>
        <input type="number" v-model="pokeId" class="form-control" placeholder="Ingresa numero de pokemon">
    </div>
    <div class="card card-body">
        {{ JSON.stringify(pokeRespuesta?.name)}}
        {{ JSON.stringify(pokeRespuesta?.sprites.front_default)}}
    </div>
    
</template>

<script setup lang="ts">

import { ref, watch } from "vue"

const pokeId = ref(0)
const pokeRespuesta = ref<any>()


const getPokemon = async () => {
    if (!pokeId) return
    const url = `https://pokeapi.co/api/v2/pokemon/${pokeId.value}/`
    const response = await fetch(url)
    console.log("getPokemon", url)
    
    pokeRespuesta.value = await response.json()
    

    
}


watch(pokeId, getPokemon)

</script>

<style scoped></style>