<template>
  <div>
    <v-container>
      <v-form ref="form" v-model="valid" onsubmit="return false">
        <v-container>
          <v-row>
            <v-col cols="12"><h1>การบ้าน/งานที่ได้รับมอบหมาย</h1> </v-col>
            <v-col cols="12" sm="5" md="5">
              <v-select
                v-model="subject"
                :items="items"
                label="กรุณาเลือกหัวข้อ"
                data-vv-name="กรุณาเลือกหัวข้อ"
                depressed
                dense
                outlined
                :rules="[(v) => !!v || 'Item is required']"
                required
              ></v-select>
            </v-col>
            <v-col cols="12" sm="5" md="5">
              <v-text-field
                v-model="content"
                label="ชื่องาน"
                placeholder="กรอกด้วยนะจ่ะ"
                outlined
                :rules="nameRules"
                dense
                required
              ></v-text-field>
            </v-col>
            <v-col cols="12" sm="2" md="2"
              ><v-btn
                color="primary"
                type="submit"
                :disabled="!valid"
                class="mr-4"
                @click="validate"
              >
                Add
              </v-btn></v-col
            >
          </v-row>
        </v-container>
      </v-form>
    </v-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [
        "Web",
        "SA",
        "ML",
        "Math",
        "AI",
        "Android",
        "IOS",
        "Blockchain",
        "Cloud",
        "Big Data",
        "Data Science",
        "Statistic",
      ],
      subject: "",
      content: "",
      valid: true,
      name: "",
      nameRules: [(v) => !!v || "Name is required"],
      select: null,
      checkbox: false,
    };
  },
  methods: {
    validate() {
      this.$emit("rtb", this.subject, this.content);
      this.$refs.form.reset();
    },
    reset() {},
    resetValidation() {
      this.$refs.form.resetValidation();
    },
  },
};
</script>

<style></style>
