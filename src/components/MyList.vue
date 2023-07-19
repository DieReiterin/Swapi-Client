<template>
  <v-window-item :value="listType">
    <v-container class="px-0 py-0">
      <v-row dense>
        <v-col v-if="this.listType === 'isLoading'" cols="4" v-for="i of 12">
          <v-card class="loader" height="160" color="secondary" theme="dark">
          </v-card>
        </v-col>
        <v-col v-else cols="4" v-for="i of this.list.results">
          <v-card height="160" color="transparent" theme="dark">
            <div class="d-flex flex-no-wrap justify-space-between">
              <div class="d-flex flex-column align-start">
                <v-card-text class="text-h6 px-2 pb-0 text-left">
                  {{ i.name }}
                </v-card-text>

                <v-card-text
                  width="150"
                  class="text-subtitle-2 px-3 py-1 text-left"
                >
                  {{
                    i.starship_class
                      ? i.starship_class
                      : i.terrain
                      ? i.terrain
                      : i.gender === "n/a"
                      ? "droid"
                      : i.gender
                  }}
                </v-card-text>

                <v-card-actions>
                  <v-btn
                    @click="
                      showDialog = true;
                      currentData = {...i};
                    "
                    class="mt-auto"
                    variant="outlined"
                    size="small"
                  >
                    ABOUT
                  </v-btn>
                </v-card-actions>
              </div>

              <v-avatar class="ma-3" size="125" rounded="0">
                <v-img :src="'assets/' + listType + '/' + i.name + '.jpeg'">
                  <template v-slot:error>
                    <v-img :src="'assets/no-image.png'">
                    </v-img>
                  </template>
                </v-img>
              </v-avatar>
            </div>
          </v-card>
        </v-col>
        <v-dialog v-model="showDialog" width="1000" height="auto">
          <v-card color="secondary" theme="dark">
            <v-card-text>
              <v-row class="py-6">
                <v-img width="600" height="400" :src="'assets/' + listType + '/' + currentData.name + '.jpeg'">

                  <template v-slot:error>
                    <v-img :src="'assets/no-image.png'">
                    </v-img>
                  </template>
                </v-img>
              </v-row>
              <v-row>
                <v-col>
                  <v-card-text class="text-h4 px-2 pb-0 text-center">
                    {{ currentData.name }}
                  </v-card-text>
                  <v-col>

                </v-col>
                <v-card-text class="text-h4 px-2 pb-5 text-left" >
                    About
                  </v-card-text>

                <v-card-text v-for="m of currentData"
                  width="400"
                  height="50"
                  class="text-subtitle-2 px-3 py-1 text-left"
                >{{ m }}
                </v-card-text>
                </v-col>
              </v-row>
            </v-card-text>
            <v-card-actions>
              <v-btn color="primary" block @click="showDialog = false"
                >Back</v-btn
              >
            </v-card-actions>
          </v-card>
        </v-dialog>
      </v-row>
    </v-container>
  </v-window-item>

</template>

<script>
import MyDialog from "@/components/MyDialog.vue";
export default {
  data() {
    return {
      showDialog: false,
      // thisTitle: '',
      currentData: [],
    };
  },
  components: {
    MyDialog,
  },
  props: {
    listType: "isLoading",
    list: [],
  },
  // methods: {
  //   startModal(info) {
  //     this.modalShow = true;
  //     return info
  //   }
  // }
};
</script>

<style scoped>
@keyframes loading {
  to {
    transform: translate(100%);
  }
}
.loader {
  /* height: 150px;
  border-radius: 0; */
  align-items: center;
  display: flex;
  flex: 1 1 100%;
  flex-wrap: wrap;
  overflow: hidden;
  position: relative;
  /* z-index: 0; */
}
.loader::after {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  animation: loading 1.5s infinite;
  background: linear-gradient(
    90deg,
    rgba(var(--v-theme-surface), 0),
    rgba(var(--v-theme-surface), 0.3),
    rgba(var(--v-theme-surface), 0)
  );
  transform: translate(-100%);
  z-index: 1;
}
</style>
