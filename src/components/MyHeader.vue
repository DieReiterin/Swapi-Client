<template>
  <v-toolbar class="header text-white" color="transparent">
    <!-- <v-app-bar-nav-icon></v-app-bar-nav-icon> -->

    <!-- <v-toolbar-title>SWAPI-Client</v-toolbar-title> -->
    <v-spacer></v-spacer>
    <h1>API Client</h1>
    <v-img :src="'/public/assets/header-logo.jpeg'">
    <!-- <v-img :src="require('public/assets/header-logo.jpeg')"> -->
      <template v-slot:error>
        <v-img :src="'/public/assets/no-image.png'"></v-img>
      </template>
    </v-img>
    <h1>API Client</h1>
    <v-spacer></v-spacer>
    <!-- <v-btn icon>
      <v-icon></v-icon>
    </v-btn> -->
  </v-toolbar>
</template>

<script>
//
</script>

<style scoped>
.header {
  height: 100px;
  margin-bottom: 20px;
  /* background: linear-gradient(rgba(0, 0, 255, 0.5), blue, transparent); */
}
</style>
