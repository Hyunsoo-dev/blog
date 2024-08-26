<template>
  <div v-if="pending">Loading...</div>
  <div v-else-if="error">Error: {{ error.message }}</div>
  <div v-else>
    <ul>
      <li v-for="post in postList" :key="post.id">
        {{ post.title }}
      </li>
    </ul>
  </div>
</template>
<script setup lang="ts">
const { pending, error, data } = await useAsyncData('posts', () =>
  queryContent().find()
);
// const data = await queryContent('/').find();
console.log('data => ', data, data.value);
const postList = computed(() =>
  data.value.map((item, idx) => ({
    id: idx,
    title: item.title,
    date: item.date,
    description: item.description,
  }))
);
console.log('postList => ', postList);
</script>
