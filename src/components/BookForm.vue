<template>
  <form @submit.prevent="submitForm" class="space-y-4 bg-white p-6 rounded-2xl shadow-md">
    <div>
      <label class="block text-sm font-medium text-gray-700">タイトル</label>
      <input v-model="title" type="text" placeholder="例: 君の名は"
        class="w-full mt-1 p-2 border rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-400">
    </div>
    <div>
      <label class="block text-sm font-medium text-gray-700">感想</label>
      <textarea v-model="review" rows="4" placeholder="読んだ感想を書く..."
        class="w-full mt-1 p-2 border rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-400"></textarea>
    </div>
    <div>
      <label class="block text-sm font-medium text-gray-700">評価（1〜5）</label>
      <input v-model.number="rating" type="number" min="1" max="5"
        class="w-full mt-1 p-2 border rounded-md focus:outline-none focus:ring-2 focus:ring-indigo-400">
    </div>
    <button type="submit"
      class="w-full bg-indigo-500 text-white py-2 rounded-md hover:bg-indigo-600 transition">追加する</button>
  </form>
</template>

<script setup>
import { ref } from 'vue'

const title = ref('')
const review = ref('')
const rating = ref(3)

const emit = defineEmits(['add-book'])

const submitForm = () => {
  if (!title.value || !review.value) return
  emit('add-book', {
    title: title.value,
    review: review.value,
    rating: rating.value
  })
  title.value = ''
  review.value = ''
  rating.value = 3
}
</script>
