<script setup>
import { computed, reactive } from 'vue'

const members = reactive([
  {
    id: 1,
    name: 'Sarah',
    age: 30,
    books: [
      {
        title: 'Lorem ipsum',
        numOfPages: 352
      },
      {
        title: 'Totam perspiciatis',
        numOfPages: 3057
      },
      {
        title: 'Distin lipsum',
        numOfPages: 120
      }
    ]
  },
  {
    id: 2,
    name: 'Olivier',
    age: 14,
    books: [
      {
        title: 'Distinctio',
        numOfPages: 873
      },
      {
        title: 'Totam perspiciatis',
        numOfPages: 3057
      }
    ]
  },
  {
    id: 3,
    name: 'Sam',
    age: 42,
    books: [
      {
        title: 'Numquam volup',
        numOfPages: 1309
      },
      {
        title: 'Lorem ipsum',
        numOfPages: 479
      },
      {
        title: 'Ipsum soluta',
        numOfPages: 1468
      },
      {
        title: 'Voluptatibus',
        numOfPages: 3801
      }
    ]
  }
])
const numberOfMember = computed(() => {
  let totalMember = members.length

  return totalMember
})
const numberOfBook = computed(() => {
  let totalBook = 0

  for (let i = 0; i < members.length; i++) {
    totalBook += members[i].books.length
  }

  return totalBook
})
const numberOfPage = computed(() => {
  let totalPage = 0

  for (let i = 0; i < members.length; i++) {
    for (let j = 0; j < members[i].books.length; j++) {
      totalPage += members[i].books[j].numOfPages
    }
  }

  return totalPage
})
// console.log('Computed value ==> ', numberOfPages.value)

const addMember = () => {
  members.push({
    id: 4,
    name: 'John',
    age: 33,
    books: [
      {
        title: 'Lorem ipsum',
        numOfPages: 352
      },
      {
        title: 'Totam perspiciatis',
        numOfPages: 3057
      }
    ]
  })
}
</script>
<template>
  <div>
    <p>Le groupe de lecture compte {{ numberOfMember }} membres</p>
    <p>
      A eux {{ numberOfMember }}, ils ont lu {{ numberOfBook }} livres pour un total de
      {{ numberOfPage }}
      pages
    </p>
    <button @click="addMember">Ajouter un membre</button>
  </div>
</template>
<style scoped></style>
