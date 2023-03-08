<template>
    <div class="w-50 mx-auto mb-2">
        <div class="input-group">
        <input type="number" v-model="pokeId" class="form-control" placeholder="Ingresa numero de pokemon">
        <button class="btn btn-primary" @click="() => $emit('emitPokeId', pokeId)">Emitir evento</button>
    </div>
    </div>
    <div class="card mb-3 w-50 mx-auto">
        <div class="row">
            <div class="col-4">
                <img :src="pokeRespuesta?.sprites.front_default" width="200" height="200"
                    style="background-color:#90ee90 ;">
            </div>
            <div class="col-8">
                <div class="card card-body">
                    <h5 class="card-title">{{ pokeRespuesta?.name }}</h5>
                    <p class="card-text">Ability: {{ pokeRespuesta?.abilities[0].ability.name }}</p>
                    <p class="card-text"><small class="text-muted">{{ pokeAbility?.effect_entries[1].effect }}</small></p>
                    <p class="card-text">Type: {{ pokeRespuesta?.types[0].type.name }}</p>
                    <p class="card-text">Move of Type: {{ pokeTypes?.moves[0].name }}</p>
                    <p class="card-text"><small class="text-muted"> Power: {{ pokeMoves?.power }}</small></p>
                    <p class="card-text"><small class="text-muted">{{ pokeMoves?.effect_entries[0].effect }}</small></p>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">

import { ref, watch, onMounted } from "vue"

const pokeId = ref(10)
const pokeRespuesta = ref<any>()
const pokeAbility = ref<any>()
const pokeTypes = ref<any>()
const pokeMoves = ref<any>()

const emit = defineEmits<{(e: 'emitPokeId', v: number): void}>()
const getPokemon = async () => {
    if (!pokeId) return
    const url = `https://pokeapi.co/api/v2/pokemon/${pokeId.value}/`
    const response = await fetch(url)
    pokeRespuesta.value = await response.json()

    const abilityId = pokeRespuesta.value.abilities[0].ability.name
    const url1 = `https://pokeapi.co/api/v2/ability/${abilityId}/`
    const response1 = await fetch(url1)
    pokeAbility.value = await response1.json()

    const typeId = pokeRespuesta.value.types[0].type.name
    const url2 = `https://pokeapi.co/api/v2/type/${typeId}/`
    const response2 = await fetch(url2)
    pokeTypes.value = await response2.json()


    const moveId = pokeTypes.value.moves[0].name
    const url3 = `https://pokeapi.co/api/v2/move/${moveId}/`
    const response3 = await fetch(url3)
    pokeMoves.value = await response3.json()
}


watch(pokeId, getPokemon)
onMounted(getPokemon)
</script>

<style scoped></style>