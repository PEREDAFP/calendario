<script setup lang="ts">
import calendarioMes from './components/calendarioMes.vue';
import { ref } from 'vue'
const mes = ref(1)
const anio = ref(2023)
</script>
<template>
    <div>Pantalla principal
        <input type="number" v-model="mes" min="1" max="12"/>
        <input type="number" v-model="anio" min="2000" max="2050"/>
    </div>
    <calendarioMes :mes="mes" :anio="anio" />
</template>

<style>

</style>