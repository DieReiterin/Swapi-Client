<template>
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
</template>

<script>
export default {
  // props: {
  //   modalData: [],
  //   listType: '',
  // }
  // methods: {
  //   openInNewTab(url) {
  //     window.open(url, '_blank', 'noreferrer');
  //   },
  // },
};
</script>

<style scoped>
/* .footer {
  background: linear-gradient(transparent, rgba(0, 0, 255, 0.5), blue);
} */
</style>
