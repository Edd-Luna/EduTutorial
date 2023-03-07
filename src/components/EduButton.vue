<template>
    <div class="my-4">
<h6>Hola desde mi primer componente <span class = text-primary >{{ counter }}</span></h6>

<div class="btn-group">
<button class="btn btn-success" @click="() => counter += 1"> Aumentar </button>
<button class="btn btn-success" @click="() => counter = 0">Reiniciar</button>
</div>
    </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const counter = ref(0)

</script>

<style scoped>

</style>