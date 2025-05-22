<template>
  <div>
    <h2>📖 登録された本</h2>
    <div v-if="books.length === 0">まだ登録されていません。</div>
    <ul>
      <li v-for="(book, index) in books" :key="index">
        <strong>{{ book.title }}</strong>（評価: {{ book.rating }}）<br />
        <em>{{ book.review }}</em>
      </li>
    </ul>
  </div>
</template>

<script setup>
defineProps({
  books: Array
})
</script>
