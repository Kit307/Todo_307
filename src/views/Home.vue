<template>
  <div>
    <hello-world />
    <Footer></Footer>
  </div>
</template>

<script>
import HelloWorld from "../components/HelloWorld";
import Footer from "../components/Footer.vue";
export default {
  name: "Home",

  components: {
    HelloWorld,
    Footer,
  },
};
</script>
