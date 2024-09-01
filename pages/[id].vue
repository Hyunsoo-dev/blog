<template>
  <main>
    <ContentDoc :path="paramsId"></ContentDoc>
  </main>
</template>
<script setup lang="ts">
definePageMeta({
  layout: 'post',
});
const route = useRoute();
const paramsId = route.params.id as string;
</script>
