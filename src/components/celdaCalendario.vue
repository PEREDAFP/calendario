<script setup lang="ts">

interface Props {
  c:number
  r:number
}

const { c, r } =  defineProps<Props>()


</script>

<template>
   <div>
    <p>{{ c }}</p>
    <p> {{ r }}</p>
   </div>
</template>

<style>
.cell, .cell input {
  height: 1.5em;
  line-height: 1.5;
  font-size: 15px;
}

.cell span {
  padding: 0 6px;
}

.cell input {
  width: 100%;
  box-sizing: border-box;
}
</style>