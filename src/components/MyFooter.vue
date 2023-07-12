<template>
  <v-toolbar class="footer text-white pb-5" color="transparent">
    <v-spacer></v-spacer>

    <v-btn class="mt-auto" variant="outlined" size="small" @click="openInNewTab('https://github.com/DieReiterin?tab=repositories')">
      My other projects on GitHub
    </v-btn>

    <v-spacer></v-spacer>
  </v-toolbar>
</template>

<script>
export default {
  methods: {
    openInNewTab(url) {
      window.open(url, '_blank', 'noreferrer');
    },
  },
};
</script>

<style scoped>
.footer {
  /* height: 150px; */
  background: linear-gradient(transparent, rgba(0, 0, 255, 0.5), blue);
}
</style>
