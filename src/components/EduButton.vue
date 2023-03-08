<template>
    <div class="my-4">
        <h6>Hola Jefecito <span class=text-primary>{{ counter }}</span></h6>
        <div class="btn-group">
            <button class="btn btn-success" @click="() => counter += 1"> Aumentar </button>
            <button class="btn btn-success" @click="() => counter = 0">Reiniciar</button>
        </div>
    </div>
        <h5>Props String <span class=text-success>{{ stringProp }} </span></h5>
        <h5>Props Component</h5>
        <code>
            {{ JSON.stringify(comp) }}
        </code>

</template>

<script setup lang="ts">
import { ref, watch } from 'vue';

// El hecho de que sea una compiler macro implica que NO debes importarla explicitamente
// Hay varias formas de declarar props pero hacerlo desde los tipos es la más 
// práctica si estamos codeando en TS.
// Dentro del bloque Script las props están disponibles como propiedades del objeto props.
// Dentro del bloque template están disponibles por su nombre
// P.EJ: aquí usaríamos props.stringProp para referirnos a lo que en el template nos referiríamos
// como stringProp
const props = defineProps<{ stringProp: string, comp: Object }>()
const emit = defineEmits<{(e: 'biteAss'): void}>()

watch(() => props.stringProp, () => {
    console.log("StringProp cambió", props.stringProp)
})

const counter = ref(0)

</script>

<style scoped></style>