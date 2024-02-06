<script setup lang="ts">
import { reactive } from 'vue'
import celdaCalendario from '@/components/celdaCalendario.vue'


interface Props{
    cols?:string[]
    COLS?:number
    ROWS?:number
}
const { cols, COLS, ROWS } = withDefaults(defineProps<Props>(),{
            cols: ()=> ['Lunes', 'Martes', 'Miércoles', 'Jueves','Viernes','Sábado', 'Domingo'],
            COLS: 7,
            ROWS: 6	
       })


const celdas = reactive(
  Array.from(Array(COLS).keys()).map(() =>
    Array.from(Array(ROWS).keys()).map(() => '')
  )
)

</script>

<template>
  <table>
    <thead>
      <tr>
        <th></th>
        <th v-for="c in cols" :key="c">{{ c }}</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="i in celdas[0].length" :key="i">
        <th>{{ i - 1 }}</th>
        <td v-for="(c, j) in cols" :key="c">
          <celdaCalendario :r="i - 1" :c="j"/>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<style>
body {
  margin: 0;
}

table {
  border-collapse: collapse;
  table-layout: fixed;
  width: 100%;
}

th {
  background-color: #eee;
}

tr:first-of-type th {
  width: 100px;
}

tr:first-of-type th:first-of-type {
  width: 25px;
}

td {
  border: 1px solid #ccc;
  height: 1.5em;
  overflow: hidden;
}
</style>