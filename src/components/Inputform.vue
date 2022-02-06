<template>
  <div>
    <v-container>
      {{ date == null }}
      {{ !valid || date == null }}
      <v-form ref="form" v-model="valid" onsubmit="return false">
        <v-container>
          <v-row>
            <v-col cols="12"><h1>การบ้าน/งานที่ได้รับมอบหมาย</h1> </v-col>
            <v-col cols="12" sm="5" md="6">
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
            <v-col cols="12" sm="5" md="6">
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

            <v-col cols="12" sm="6" md="6">
              <v-dialog
                ref="dialog"
                v-model="modal"
                :return-value.sync="date"
                persistent
                dense
                solo
                width="290px"
              >
                <template v-slot:activator="{ on, attrs }">
                  <v-text-field
                    v-model="date"
                    label="Picker in dialog"
                    prepend-icon="mdi-calendar"
                    readonly
                    v-bind="attrs"
                    v-on="on"
                  ></v-text-field>
                </template>
                <v-date-picker v-model="date" scrollable>
                  <v-spacer></v-spacer>
                  <v-btn
                    text
                    color="primary"
                    @click="
                      modal = false;
                      valid = false;
                    "
                  >
                    Cancel
                  </v-btn>
                  <v-btn text color="primary" @click="$refs.dialog.save(date)">
                    OK
                  </v-btn>
                </v-date-picker>
              </v-dialog>
            </v-col>
            <v-col cols="12" sm="2" md="1"
              ><v-btn
                color="primary"
                type="submit"
                :disabled="!valid || date == null"
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
      modal: false,
      date: "",
    };
  },
  methods: {
    validate() {
      this.$emit("rtb", this.subject, this.content, this.date);
      this.$refs.form.reset();
      this.valid = true;
    },
    reset() {},
    resetValidation() {
      this.$refs.form.resetValidation();
    },
  },
};
</script>

<style></style>
