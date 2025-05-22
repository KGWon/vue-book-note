<template>
  <form @submit.prevent="submitBook">
    <div>
      <label>タイトル：</label>
      <input v-model="title" required />
    </div>
    <div>
      <label>感想：</label>
      <textarea v-model="review"></textarea>
    </div>
    <div>
      <label>評価（1〜5）：</label>
      <input type="number" v-model.number="rating" min="1" max="5" />
    </div>
    <button type="submit">登録</button>
  </form>
</template>

<script setup>
import { ref } from 'vue'

const emit = defineEmits(['add-book'])

const title = ref('')
const review = ref('')
const rating = ref(3)

const submitBook = () => {
  emit('add-book', {
    title: title.value,
    review: review.value,
    rating: rating.value,
  })
  title.value = ''
  review.value = ''
  rating.value = 3
}
</script>
