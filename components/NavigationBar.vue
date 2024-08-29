<template>
  <v-toolbar
    dark="true"
    color="white"
    elevation="4"
    density="compact"
    class="container"
  >
    <v-toolbar-title>에블</v-toolbar-title>
    <v-spacer></v-spacer>
    <v-btn><NuxtLink to="/">Resume</NuxtLink></v-btn>
    <v-btn><NuxtLink to="/posts">Posts</NuxtLink></v-btn>
  </v-toolbar>
</template>

<style lang="scss" scoped>
.container {
  // top: 0;
  // height: 50px;
  // position: absolute;
}
</style>
