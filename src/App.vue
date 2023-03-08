<script setup lang="ts">

import { ref } from "vue";
import EduButton from './components/EduButton.vue';
import EduStrings from './components/EduStrings.vue';
import EduInput from './components/EduInput.vue';
import PokeSelector from "./components/PokeSelector.vue";

const stringEjemplo = ref('')
const memoriaConteo = ref(0)

setInterval(() => {stringEjemplo.value += '#'}, 5000)

const customEventHandler = (event) => {
  document.title = event
}

</script>

<template>
  <PokeSelector @emit-poke-id="customEventHandler($event)"></PokeSelector>
  <div class="card card-body w-50 mx-auto mt-4 bg-info p-2 text-dark bg-opacity-25" >
  <h4>Cantidad previa {{ memoriaConteo }}</h4>
<EduButton :string-prop="stringEjemplo" :comp="{a:  'a1', b: 'b2'}"  @bite-ass="($event) => {memoriaConteo =$event}"></EduButton>
<EduStrings :number-prop= "3.1416"></EduStrings>
<EduInput></EduInput>
</div>
</template>

<style scoped>

</style>
