<template>
  <div>
    <v-app>
      <NavigationBar />
      <v-sheet
        class="pa-4"
        color="grey lighten-2"
        :class="responsiveWidthClass"
      >
        <NuxtPage />
      </v-sheet>
    </v-app>
  </div>
</template>

<script setup lang="ts">
import { useDisplay } from "vuetify";
const vuetify = useDisplay();
console.log("vuetify:", vuetify);

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
<style scoped>
.w-100 {
  width: 100%;
}
.w-50 {
  width: 50%;
}
.w-33 {
  width: 33.33%;
}
.w-25 {
  width: 25%;
}
.w-20 {
  width: 20%;
}
</style>
