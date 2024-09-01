<template>
  <v-toolbar
    dark="true"
    color="white"
    elevation="4"
    density="compact"
    class="container"
  >
    <v-toolbar-title @click="router.push('/')">에블</v-toolbar-title>
    <v-spacer></v-spacer>
    <v-btn><NuxtLink to="/">Posts</NuxtLink></v-btn>
  </v-toolbar>
</template>
<script setup lang="ts">
const router = useRouter();
</script>
<style lang="scss" scoped>
.container {
  top: 0;
  height: 50px;
  position: sticky;
  z-index: 1;
}
</style>
