<template>
    <div class="my-4">
        <h6>Hola desde mi primer string <span class=text-primary>{{ strings }}</span></h6>
        <div class="btn-group">
            <button class="btn btn-danger" @click="() => strings += '1'"> Agregar </button>
            <button class="btn btn-danger" @click="() => strings = '1'"> Reiniciar</button>
        </div>
    </div>
        <h5> Props numbers <span class=text-success>{{ numberProp }}</span></h5>
</template>

<script setup lang="ts">
import { ref } from 'vue';
const props = defineProps<{ numberProp: number}>()
const strings = ref("1")
</script>

<style scoped></style>