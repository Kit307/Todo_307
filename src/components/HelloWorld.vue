<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="12">
        <v-img
          :src="require('../assets/k.png')"
          class="my-3"
          contain
          height="200"
        />
      </v-col>
    </v-row>
    <div class="text-center mt-5" style="font-size: 5rem">
      งานอยู่ตรง Todo นะ
    </div>
  </v-container>
</template>

<script>
export default {
  name: "HelloWorld",

  data: () => ({}),
};
</script>
