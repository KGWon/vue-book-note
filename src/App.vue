<template>
  <main class="min-h-screen bg-gray-100 p-6">
    <div class="max-w-xl mx-auto">
      <h1 class="text-3xl font-bold text-center text-indigo-600 mb-8">📚 読書記録アプリ</h1>
      <BookForm @add-book="addBook" />
      <BookList :books="books" />
    </div>
  </main>
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
