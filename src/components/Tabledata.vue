<template>
  <v-container fluid>
    <div class="d-flex flex-wrap">
      <div v-for="(item, i) in name" :key="i">
        <div v-if="item.complete">
          <v-hover v-slot="{ hover }" close-delay="200">
            <v-card
              :elevation="hover ? 16 : 5"
              :class="{ 'on-hover': hover }"
              class="mx-5 mt-5"
              min-width="300"
              max-width="500"
              outlined
              color="#0277BD"
            >
              <v-card-text class="white--text">
                <div class="text-h5 mb-4">
                  <span class=""
                    ><v-btn color="success" fab x-small>
                      <h1>{{ i + 1 }}</h1>
                    </v-btn></span
                  >
                  {{ "  " + item.name }}
                </div>
                <p class="subtitle-1">{{ "รายละเอียด  :" + item.conten }}</p>
              </v-card-text>
              <v-card-actions>
                <v-btn
                  rounded
                  color="red lighten-1 white--text"
                  @click="deletestu(i)"
                >
                  Delete
                </v-btn>
                <v-card-text>
                  <v-chip class="deep-purple accent-4 white--text">{{
                    item.date
                  }}</v-chip>
                </v-card-text>
              </v-card-actions>
            </v-card>
          </v-hover>
        </div>
        <div v-else>
          <v-hover v-slot="{ hover }" close-delay="200">
            <v-card
              :elevation="hover ? 16 : 5"
              :class="{ 'on-hover': hover }"
              class="mx-5 mt-5"
              min-width="300"
              max-width="500"
              outlined
              color=""
            >
              <v-card-text class="black--text">
                <div class="text-h5 mb-4">
                  <span class=""
                    ><v-btn color="success" fab x-small>
                      <h1>{{ i + 1 }}</h1>
                    </v-btn></span
                  >
                  {{ "  " + item.name }}
                </div>
                <p class="subtitle-1">{{ "รายละเอียด  :" + item.conten }}</p>
              </v-card-text>
              <v-card-actions>
                <v-btn rounded color="primary" @click="com(i)">
                  complete
                </v-btn>
                <v-btn
                  rounded
                  color="red lighten-1 white--text"
                  @click="deletestu(i)"
                >
                  Delete
                </v-btn>
                <v-card-text>
                  <v-chip class="deep-purple accent-4 white--text">{{
                    item.date
                  }}</v-chip>
                </v-card-text>
              </v-card-actions>
            </v-card>
          </v-hover>
        </div>
      </div>
    </div>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      // items1: [
      //   { text: "วิชา Web Assignment1" },
      //   { text: "วิชา ML Assignment1" },
      //   { text: "วิชา ML ออกแบบ" },
      // ],
      // green: "#26c6da",
    };
  },
  props: ["name"],
  methods: {
    deletestu(i) {
      this.name.splice(i, 1);
    },
    com(i) {
      this.name[i].complete = true;
    },
  },
};
</script>

<style></style>
