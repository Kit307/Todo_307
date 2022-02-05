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
              <v-list-item three-line>
                <v-list-item-content>
                  <div class="text-h5 mb-4 white--text">
                    {{ i + 1 + "  " }}{{ item.name }}
                  </div>
                  <v-list-item-subtitle class="white--text">{{
                    "รายละเอียด  :" + item.conten
                  }}</v-list-item-subtitle>
                </v-list-item-content>
              </v-list-item>

              <v-card-actions>
                <v-btn
                  rounded
                  color="red lighten-1 white--text"
                  @click="deletestu(i)"
                >
                  Delete
                </v-btn>
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
              <v-list-item three-line>
                <v-list-item-content>
                  <div class="text-h5 mb-4">
                    {{ i + 1 + "  " }}{{ item.name }}
                  </div>
                  <v-list-item-subtitle>{{
                    "รายละเอียด  :" + item.conten
                  }}</v-list-item-subtitle>
                </v-list-item-content>
              </v-list-item>

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
