<script setup lang="ts">
import { reactive } from 'vue'
import celdaCalendario from '@/components/celdaCalendario.vue'


interface Props{
    mes:string
    anio:string
    cols?:string[]
    COLS?:number
    ROWS?:number
}
const { mes, anio,cols, COLS, ROWS } = withDefaults(defineProps<Props>(),{
            cols: ()=> ['Lunes', 'Martes', 'Miércoles', 'Jueves','Viernes','Sábado', 'Domingo'],
            COLS: 7,
            ROWS: 6	
       })


const celdas = reactive(
  Array.from(Array(COLS).keys()).map(() =>
    Array.from(Array(ROWS).keys()).map(() => '- ')
  )
)
const getWeekDay:(date: Date)=>number  = (date: Date) => {
  let days = [6,0,1,2,3,4,5]
  return days[date.getDay()];
}
const primerdia = new Date(`${mes}/01/${anio}`)
console.log(primerdia)
console.log(getWeekDay(primerdia))

console.log(celdas)
celdas[0][getWeekDay(primerdia)]=`${mes}/01/${anio}`



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
          <celdaCalendario :r="i - 1" :c="j" :contenido="celdas[i-1][j]"/>
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