<script >
import { ref, reactive } from 'vue'

export default {
  setup() {
    const arr = reactive([]);
    const myInput = ref('')
    const inputValue = myInput;
   
    function addText(){
      if(this.myInput == '') {
        return
      }
      else {
        // arr.push(this.myInput.charAt(0).toUpperCase() + this.myInput.slice(1))
        arr.push(this.myInput.toUpperCase())
        this.myInput = ''
      }
    }
    function setValue() {
      if(inputValue.value.length < 11) {
        this.myInput = inputValue.value
      }
      else {
        this.myInput = ''
      }
    }
   return {
    arr, myInput, inputValue,
    addText, setValue,
   }
  }
}

// const arr = reactive([]);
// const myInput = ref('')
// const inputValue = myInput;

// function addText(){
//   if(this.myInput == '') {
//     return
//   }
//   else {
// //  arr.push(this.myInput.charAt(0).toUpperCase() + this.myInput.slice(1))
//     arr.push(this.myInput.toUpperCase())
//     this.myInput = ''
//   }
// }

// function setValue() {
//   if(inputValue.value.length < 11) {
//     this.myInput = inputValue.value
//   }
//   else {
//     this.myInput = ''
//   }
// }

</script>

<template>
  <h1 :style="{
    color: myInput.length <= 4 ? 'red' : 'blue'
  }">Список задач</h1>
  <input v-model="myInput" @keyup.enter="addText()" @input="setValue()" >
  <button @click="addText()">Добавить</button>
  <p v-if="arr.length">
    <p v-for="(elem, index) in arr" :key="elem" :style="{color: elem.length <= 5 ? 'black' : 'green'}">({{index+1}}) {{elem}} 
      <button @click="arr.splice(index, 1)">Удалить</button>
    </p>
    <p>Всего записей: {{arr.length}}. Удовоенное: {{arr.length*2}}</p>
  </p>
  <p v-else>Записей нет</p>
</template>

<style scoped lang="sass">
@use "sass:math"
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
