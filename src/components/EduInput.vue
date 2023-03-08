<template>
    <div class="my-4 input-group">
        <input class="form-control" type="text" v-model="inputText">
        <button class="btn btn-warning" @click="() => titleText = inputText">Publicar</button>
        <button class="btn btn-warning" @click="() => titleText = '' ">Borrar</button>
    </div>
    <div class="badge bg-primary text-wrap text-center mx-auto mt-4" style="width: 20rem; min-height: 5rem;">
        <h2 >{{ titleText }} 3</h2>
    </div>
</template>

<script setup lang="ts">
import { ref } from "vue"

const inputText = ref('')
const titleText = ref('')



</script>

<style scoped></style>