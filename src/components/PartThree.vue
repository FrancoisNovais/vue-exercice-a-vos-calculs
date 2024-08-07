<script setup>
import { ref, computed } from 'vue'

const user = {
  firstName: 'Toto',
  lastName: 'Smith'
}

const currentTime = ref(new Date().getHours())

const message = computed(() => {
  let text = ''

  if (currentTime.value < 12) {
    text = 'Bonjour'
  } else if (currentTime.value < 18) {
    text = 'Bon après-midi'
  } else {
    text = 'Bonsoir'
  }

  return text + ' ' + user.firstName + ' ' + user.lastName + ' !'
})
</script>
<template>
  <div>
    <p>{{ message }}</p>
    <button @click="currentTime = 0">Heure matin</button>
    <button @click="currentTime = 12">Heure aprèm</button>
    <button @click="currentTime = 18">Heure soir</button>
  </div>
</template>
<style scoped></style>
