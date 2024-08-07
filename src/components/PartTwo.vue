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
const numberOfMembers = computed(() => {
  let totalMembers = members.length

  return totalMembers
})
const numberOfBooks = computed(() => {
  let totalBooks = 0

  for (let i = 0; i < members.length; i++) {
    totalBooks += members[i].books.length
  }

  return totalBooks
})
const numberOfPages = computed(() => {
  let totalPages = 0

  for (let i = 0; i < members.length; i++) {
    for (let j = 0; j < members[i].books.length; j++) {
      totalPages += members[i].books[j].numOfPages
    }
  }

  return totalPages
})
// console.log('Computed value ==> ', numberOfPages.value)

const addMembers = () => {
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
    <p>Le groupe de lecture compte {{ numberOfMembers }} membres</p>
    <p>
      A eux {{ numberOfMembers }}, ils ont lu {{ numberOfBooks }} livres pour un total de
      {{ numberOfPages }}
      pages
    </p>
    <button @click="addMembers">Ajouter un membre</button>
  </div>
</template>
<style scoped></style>
