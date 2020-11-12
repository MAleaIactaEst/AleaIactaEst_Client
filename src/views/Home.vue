<template>
  <v-container>
    <HomeComponent />
  </v-container>
</template>

<script>
// @ is an alias to /
import HomeComponent from "@/components/HomeComponent.vue";

export default {
  name: "Home",
  components: {
    HomeComponent,
  }
};
</script>
