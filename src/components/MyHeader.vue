<template>
  <v-toolbar class="header text-white" color="transparent">
    <v-spacer></v-spacer>
    <h1>API Client</h1>
    <v-img :src="'assets/header-logo.jpeg'">
      <template v-slot:error>
        <v-img :src="'assets/no-image.png'"></v-img>
      </template>
    </v-img>
    <h1>API Client</h1>
    <v-spacer></v-spacer>

  </v-toolbar>
</template>

<script>

</script>

<style scoped>
.header {
  height: 100px;
  margin-bottom: 20px;
}
</style>
