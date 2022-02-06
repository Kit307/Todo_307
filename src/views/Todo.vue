<template>
  <div style="min-height: 100rem;">
    <Inputform @rtb="getButton"></Inputform>
    <Tabledata :name="data"></Tabledata>
    <Footer></Footer>
  </div>
</template>

<script>
import Inputform from "../components/Inputform.vue";
import Tabledata from "../components/Tabledata.vue";
import Footer from "../components/Footer.vue";

export default {
  name: "Input",
  components: { Inputform, Tabledata, Footer },
  methods: {
    getButton(i, j, date) {
      this.data.push({
        name: "วิชา " + " " + i,
        conten: " " + j,
        date: date,
        complete: false,
      });
    },
  },
  data() {
    return {
      data: [],
    };
  },
};
</script>

<style></style>
