<script setup>
import { computed, ref } from 'vue'

const number = ref([76, 876, 467, 2, 67, 3, 90, 7, 678])

const average = computed(() => {
  let total = 0
  for (let i = 0; i < number.value.length; i++) {
    total += number.value[i]
  }
  total = total / number.value.length
  return total.toFixed(2)
})
// console.log('Computed value ==> ', average.value)

const pushRandomNumber = () => {
  const randomNum = Math.floor(Math.random() * 1000)
  //   console.log(randomNum)
  return number.value.push(randomNum)
}
</script>

<template>
  <p>Moyenne du tableau : {{ number }}</p>
  <p>{{ average }}</p>
  <button @click="pushRandomNumber">Ajouter un nombre aléatoire</button>
</template>

<style scoped></style>
