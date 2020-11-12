<template>
  <v-container class="pa-0">
    <v-app-bar
      app
      color="purple"
      dark
    >
      <div class="d-flex align-center">
        <v-tab href="/">
          <v-img
            alt="Vuetify Logo"
            class="shrink mr-2"
            contain
            src="https://www.flaticon.com/svg/static/icons/svg/3602/3602755.svg"
            transition="scale-transition"
            width="40"
          />
          <v-toolbar-title>Alea Iacta Est</v-toolbar-title>
        </v-tab>
      </div>

      <v-spacer></v-spacer>
     <v-tab href="/images">
     <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="https://www.flaticon.com/svg/static/icons/svg/685/685681.svg"
          transition="scale-transition"
          width="30"
        />
    </v-tab>

    </v-app-bar>
  </v-container>
</template>

<script>
  export default {
    name: 'NavBar'
  }
</script>
