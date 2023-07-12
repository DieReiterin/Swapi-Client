<template>
  <v-app>
    <v-container
      fluid
      class="container d-flex flex-column align-center pt-50 pb-0 px-0 text-white"
    >
      <my-header></my-header>
      <my-main></my-main>
      <my-footer></my-footer>

    </v-container>
  </v-app>
</template>

<script>
import MyHeader from '@/components/MyHeader.vue'
import MyMain from '@/components/MyMain.vue'
import MyFooter from '@/components/MyFooter.vue'
export default {
  components: {
    MyHeader,
    MyFooter,
    MyMain,
  },
};
</script>

<style>
.container {
  background: navy url("@/assets/background__main.jpeg") no-repeat center center / cover fixed;
}



</style>
