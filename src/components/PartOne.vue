<script setup>
import { computed, reactive } from 'vue'

const number = reactive([76, 876, 467, 2, 67, 3, 90, 7, 678])

const average = computed(() => {
  let total = 0
  for (let i = 0; i < number.length; i++) {
    total += number[i]
  }
  total = total / number.length
  return total
})
// console.log('Computed value ==> ', average.value)

const pushRandomNumber = () => {
  const randomNum = Math.floor(Math.random() * 1000)
  //   console.log(randomNum)
  return number.push(randomNum)
}
</script>

<template>
  <div>
    <p>Moyenne du tableau : {{ number }}</p>
    <p>{{ average.toFixed(2) }}</p>
    <button @click="pushRandomNumber">Ajouter un nombre aléatoire</button>
  </div>
</template>

<style scoped></style>
