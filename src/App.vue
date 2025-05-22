<template>
  <div class="container">
    <h1>📚 読書記録アプリ</h1>
    <BookForm @add-book="addBook" />
    <BookList :books="books" />
  </div>
</template>

<script setup>
import { ref, onMounted, watch } from 'vue'
import BookForm from './components/BookForm.vue'
import BookList from './components/BookList.vue'

const books = ref([])

onMounted(() => {
  const saved = localStorage.getItem('books')
  if (saved) {
    books.value = JSON.parse(saved)
  }
})

watch(books, (newVal) => {
  localStorage.setItem('books', JSON.stringify(newVal))
}, { deep: true })

const addBook = (book) => {
  books.value.push(book)
}
</script>

<style>
.container {
  max-width: 600px;
  margin: auto;
  padding: 1rem;
}
</style>
