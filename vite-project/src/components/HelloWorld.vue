<script setup>
import { ref, reactive } from 'vue'

// const data = reactive({symbol: ""})

let arr = reactive([]);

function addText(value){
  if(value == '') return
  arr.push(value.charAt(0).toUpperCase() + value.slice(1))
  let input = ref(value)
  input = ''
}
</script>

<template>
  <input v-model="myInput" @keyup.enter="addText(myInput)">
  <p v-if="arr.length">
    <p v-for="(elem, index) in arr" :key="elem">{{elem}}
      <button @click="arr.splice(index, 1)">Удалить</button>
    </p>
    <p>Всего записей: {{arr.length}}. Удовоенное: {{arr.length*2}}</p>
  </p>
  <p v-else>Записей нет</p>
  
  
</template>

<style scoped lang="sass">

input
  font-family: Arial, sans-serif
  background-color: gray
  border: 3px solid #FFFFFF
  font-size: 18px
  outline: none
  padding: 10px
  color: #FFFFFF
p
  font-family: Arial, sans-serif
  font-size: 18px
  color: #FFFFFF


</style>