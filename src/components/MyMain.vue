<template>
  <v-row class="main">
    <v-card width="1100" color="transparent">
      <v-tabs color="blue" class="mb-5">
        <v-spacer></v-spacer>
        <v-tab @click="this.fetchData()" value="characters" width="250"
          >Characters</v-tab
        >
        <v-tab
          @click="this.fetchData('starships')"
          value="starships"
          width="250"
          >Starships</v-tab
        >
        <v-tab @click="this.fetchData('planets')" value="planets" width="250"
          >Planets</v-tab
        >
        <v-spacer></v-spacer>
      </v-tabs>

      <v-card-text>
        <v-window v-if="this.listIsLoading">
          <my-list listType='isLoading'></my-list>
        </v-window>
        <v-window v-if="!this.listIsLoading">
          <my-list v-if="this.currentList === 'characters'" listType='characters' :list=this.myResponse></my-list>
          <my-list v-if="this.currentList === 'starships'" listType='starships' :list=this.myResponse></my-list>
          <my-list v-if="this.currentList === 'planets'" listType='planets' :list=this.myResponse></my-list>
        </v-window>
      </v-card-text>
    </v-card>

  </v-row>
</template>

<script>
import axios from "axios";
import MyList from '@/components/MyList.vue'
export default {
  components: {
    MyList,
  },
  data() {
    return {
      listIsLoading: false,
      myResponse: [],
      currentList:'characters',
    };
  },
  methods: {
    async fetchData(type = "people") {
      try {
        this.listIsLoading = true;
        this.currentList = type === "people" ? 'characters' : type;
        const response = await axios.get(`https://swapi.dev/api/${type}/`, {
          params: {
            // _page: this.page,
            // _limit: this.limit,
          },
        });
        // this.totalPages = Math.ceil(response.headers['x-total-count'] / this.limit);
        this.myResponse = response.data;
      } catch (e) {
        alert(e);
      } finally {
        this.listIsLoading = false;
      }
    },
  },
  mounted() {
    this.fetchData();
    // const options = {
    //     rootMargin: '0px',
    //     threshold: 1.0
    // };
    // const callback = (entries, observer) => {
    //     if(entries[0].isIntersecting && this.page < this.totalPages) {
    //         this.loadMorePosts()
    //     }
    // };
    // const observer = new IntersectionObserver(callback, options);
    // observer.observe(this.$refs.observer);
  },
};
</script>

<style scoped>
.main {
  /* width: 70%; */
  min-height: 390px;
  margin-bottom: 20px !important;
  /* padding: 0!important; */
  border-radius: 15px;
  text-align: center;
  /* background: rgba(0, 0, 255, 0.4); */
  background: rgba(6, 6, 68, 0.4);
  /* #060644 */
}
</style>
