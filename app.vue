<template>
  <div>
    <v-app>
      <NavigationBar />
      <NuxtLayout>
        <NuxtPage />
      </NuxtLayout>
    </v-app>
  </div>
</template>

<script setup lang="ts">
import { useDisplay } from 'vuetify';
const vuetify = useDisplay();
console.log('vuetify:', vuetify);

// const responsiveWidthClass = computed(() => {
//   const { xs, sm, md, lg, xl } = vuetify.display;
//   return {
//     "w-100": xs, // 100% width on extra small screens
//     "w-50": sm, // 50% width on small screens
//     "w-33": md, // 33.33% width on medium screens
//     "w-25": lg, // 25% width on large screens
//     "w-20": xl, // 20% width on extra large screens
//   };
// });
</script>
<style lang="scss" scoped></style>
