<template>
  <div class="grid gap-4 mt-6">
    <div v-for="(book, index) in books" :key="index"
      class="bg-white p-4 rounded-xl shadow-md hover:shadow-lg transition">
      <div class="flex justify-between items-center mb-2">
        <h2 class="text-lg font-semibold text-indigo-700">{{ book.title }}</h2>
        <span class="text-yellow-500 text-sm">⭐️ {{ book.rating }}/5</span>
      </div>
      <p class="text-gray-600 whitespace-pre-line">{{ book.review }}</p>
    </div>
  </div>
</template>

<script setup>
defineProps({
  books: {
    type: Array,
    required: true
  }
})
</script>
